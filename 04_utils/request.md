```javascript
import axios from 'axios'
import { Message } from 'element-ui'
import { getToken, removeToken, redirectLogin } from './tools'

/**
 * @description 基于axios的二次封装
 */

const Instance = axios.create({
    timeout: 60 * 1000, // 设置请求超时时间
    validateStatus: status => {
        return (status >= 200 && status < 300) || status === 401
    },
})

Instance.interceptors.request.use(
    config => {
        if (config.method === 'post') {
            config.data = {
                ...config.data,
            }
        } else if (config.method === 'get') {
            config.params = {
                ...config.params,
            }
        }
        //设置token
        config.headers.token = getToken()
        return config
    },
    error => {
        Promise.reject(error)
    },
)

Instance.interceptors.response.use(
    response => {
        const { code, message } = response.data

        if (response.status === 401 || code === 400) {
            // 移除cookie中 token ，退出登录操作
            removeToken()
            return redirectLogin()
        }

        if (code === 200) {
            //请求成功操作
            return response.data
        } else if (code) {
            Message.info({ message: message || '数据异常，请稍后再试' })
            return Promise.reject(response.data)
        } else {
            return Promise.resolve(response.data)
        }
    },
    error => {
        Message.error({ message: '服务异常，请稍后再试' })
        return Promise.reject(error)
    },
)

export default Instance


```
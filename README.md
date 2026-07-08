# dc-opentelemetry-collector-with-openobserve

OpenTelemetry Collector + OpenObserve 快速部署方案。

## 快速启动

```bash
docker compose up -d
```

## 配置说明

### OpenObserve 登录凭证

支持通过 `.env` 文件自定义管理员账号，不配置则使用默认值：

| 环境变量 | 默认值 | 说明 |
| --- | --- | --- |
| `ZO_ROOT_USER_EMAIL` | `root@example.com` | 管理员邮箱 |
| `ZO_ROOT_USER_PASSWORD` | `Complexpass#123` | 管理员密码 |

在项目根目录创建 `.env` 文件：

```
ZO_ROOT_USER_EMAIL=admin@your-domain.com
ZO_ROOT_USER_PASSWORD=your-secure-password
```

### Collector 认证 Token

`otel-collector-config.yaml` 中的 Authorization 也支持通过 `.env` 覆盖：

| 环境变量 | 默认值 |
| --- | --- |
| `OPENOBSERVE_AUTH_TOKEN` | `Basic cm9vdEBleGFtcGxlLmNvbTpDb21wbGV4cGFzcyMxMjM=` |

注意：修改 token 后，`.env` 中的 `OPENOBSERVE_AUTH_TOKEN` 应与 OpenObserve 实际的凭证保持一致，否则 Collector 无法向 OpenObserve 发送数据。

示例 `.env` 完整内容：

```
ZO_ROOT_USER_EMAIL=admin@your-domain.com
ZO_ROOT_USER_PASSWORD=your-secure-password
OPENOBSERVE_AUTH_TOKEN=Basic <your-base64-encoded-credentials>
```

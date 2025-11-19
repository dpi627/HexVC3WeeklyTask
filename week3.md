# Week 3 - Deploy to Zeabur

- fork https://github.com/gonsakon/backend-healthCheck-API
- Sign up Zeabur and sign in
- Authenticate mobile phone, google and github in settings

> [!IMPORTANT]
> ⚠️ GitHub 驗證特別重要，一定要完成

# Delopyment Service in Zeabur

- Make sure GitHub repo is ready
- Create Project on Zeabur
- Create Service in Project
- Choice repo and branch
- Wait for Service deployment

## Add Domain

- Choice Add Domain
- Public internet > Binding Zeabur Sub-Domain
- Enter an available domain name
- ex., `hex-health-check.zeabur.app`
- Copy and paste to browser, you'll see below

```json
{
  message: "歡迎使用 API 服務",
  endpoints: {
    health: "/api/health",
    products: "/api/products?min=5000&max=20000"
  }
}
```

## Test Endpoints

```sh
curl https://hex-health-check.zeabur.app/api/health
```

```json
{
  status: "OK",
  timestamp: "2025-11-19T12:23:02.262Z"
}
```

---

# 📋完成作業

- [GitHub Repository](https://github.com/dpi627/backend-healthCheck-API)
- [Zeabur Publish Url](https://hex-health-check.zeabur.app/api/health/)
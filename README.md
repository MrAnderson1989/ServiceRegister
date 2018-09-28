
# ServiceRegister
服务注册组件

## doc

配置文件

```json
"Service": {
    "Name": "OrgSvc",
    "IP": "10.1.75.52",
    "Port": "80"
  },
  "Consul": {
    "IP": "10.1.75.52",
    "Port": "8500"
  }

```

Startup.cs 添加代码
```

 app.UseHealthMiddleware();

ConsulService consulService = new ConsulService()
{
    IP = Configuration["Consul:IP"],
    Port = Convert.ToInt32(Configuration["Consul:Port"])
};

HealthService healthService = new HealthService()
{
    IP = Configuration["Service:IP"],
    Port = Convert.ToInt32(Configuration["Service:Port"]),
    Name = Configuration["Service:Name"],
};

app.RegisterConsul(lifetime, healthService, consulService);

```

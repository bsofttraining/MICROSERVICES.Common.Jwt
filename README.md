# MICROSERVICES.Common.Jwt
Extension de seguridad para microservicios  
Versión: .NET Standard 2.0  

# appsettings.json
```
"jwt": {
    "enabled": true,
    "issuer": "http://ivancuadros.com",
    "audience": "web",
    "key": "CLave#12548MIentrasMas45566Mejor____%%%dddd",
    "expiration": "30"
  }
```

# Startup.cs
```
public void ConfigureServices(IServiceCollection services)
{

    services.AddJwtCustomized();
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
    services.Configure<JwtOptions>(Configuration.GetSection("jwt"));
 }
```

# In the controller
```
public AuthController(IOptionsSnapshot<JwtOptions> jwtOption)
{
    this.jwtOption = jwtOption.Value;
}

.
.
.

Response.Headers.Add("Authorization", "Bearer " + JwtToken.Create(jwtOption));
```

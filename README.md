# SS14.Admin

SS14.Admin is the web-based admin panel intended to be used with Space Station 14.

## Configuration

Example config file:

```yml
Serilog:
    Using: [ "Serilog.Sinks.Console" ]
    MinimumLevel:
        Default: Information
        Override:
            SS14: Debug
            Microsoft: "Warning"
            Microsoft.Hosting.Lifetime: "Information"
            Microsoft.AspNetCore: Warning
            IdentityServer4: Warning
    WriteTo:
        - Name: Console
          Args:
              OutputTemplate: "[{Timestamp:HH:mm:ss} {Level:u3} {SourceContext}] {Message:lj}{NewLine}{Exception}"

    Enrich: [ "FromLogContext" ]

    #Loki:
    #    Address: "http://localhost:3102"
    #    Name: "centcomm"

ConnectionStrings:
    # Connects to the same postgres database as the game server
    DefaultConnection: "Server=127.0.0.1;Port=5432;Database=ss14;User Id=ss14-admin;Password=foobar"

AllowedHosts: "central.spacestation14.io"

urls: "http://localhost:27689/"

PathBase: "/admin"

WebRootPath: "/opt/ss14_admin/bin/wwwroot"

ForwardProxies:
    - 127.0.0.1

Auth:
    Authority: "https://central.spacestation14.io/web/"
    ClientId: "ss14-admin"
    ClientSecret: "foobar"

authServer: "https://central.spacestation14.io/auth"
```

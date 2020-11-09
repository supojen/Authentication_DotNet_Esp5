# 有關於 Secure Razor Page

<br><br>

### Razor Page 預備小知識
___
- 使用 Razor Page 時, 一定要先 Register 
    ```c#
    services.AddRazorPages(options => {
    });
    ```
- 要告訴 UseEndpoints Middelware 怎麼找到對應的 Razor Page
    ```c#
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapDefaultControllerRoute();
        endpoints.MapRazorPages();   // Here
    });
    ```
- Razor Page 要放在 Pages 資料夾內

<br><br>

### Secure Razor Page
___
* 其實就是 Register Razor Page 時, 作揖些配置
```c#
services.AddRazorPages(options => {
    options.Conventions.AuthorizePage("/Razor/Secure");                 //　Auth 配置
    options.Conventions.AuthorizePage("/Razor/Secure", "Technology.2"); //　Auth 配置
    options.Conventions.AuthorizeFolder("/SecureRazor/");               //　Auth 配置
    options.Conventions.AllowAnonymousToPage("/SecureRazor/Anon");      //　Auth 配置
});
```


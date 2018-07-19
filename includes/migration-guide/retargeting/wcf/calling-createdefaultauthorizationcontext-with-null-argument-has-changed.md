### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Wywoływanie CreateDefaultAuthorizationContext przy użyciu argumentu o wartości null został zmieniony

|   |   |
|---|---|
|Szczegóły|Implementacja <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> zwracany przez wywołanie <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> o wartości null authorizationPolicies argument zmienił jego implementacji w programie .NET Framework 4.6.|
|Sugestia|W rzadkich przypadkach aplikacje usługi WCF, które używają uwierzytelniania niestandardowego zaobserwować różnice w zachowaniu. W takich przypadkach można przywrócić poprzednie zachowanie na dwa sposoby:<ol><li>Należy ponownie skompilować aplikację pod kątem starszej wersji programu .NET Framework niż 4.6. W przypadku usług hostowanych przez usługi IIS, użyj &lt;httpRuntime targetFramework =&quot;x.x&quot;  / &gt; elementu pod kątem starszej wersji programu .NET Framework.</li><li>Dodaj następujący wiersz do <code>&lt;appSettings&gt;</code> sekcji w pliku app.config: <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Trwa przekierowywanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|


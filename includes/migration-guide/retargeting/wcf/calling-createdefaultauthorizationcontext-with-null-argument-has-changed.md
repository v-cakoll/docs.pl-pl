### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Wywoływanie metody CreateDefaultAuthorizationContext z argumentu o wartości null został zmieniony

|   |   |
|---|---|
|Szczegóły|Implementacja <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> zwrócony przez wywołanie do <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> o wartości null authorizationPolicies argument zmienił jego wykonania w .NET Framework 4.6.|
|Sugestia|W rzadkich przypadkach aplikacji WCF, które używają uwierzytelniania niestandardowego może wystąpić różnice funkcjonalne. W takich przypadkach można przywrócić poprzedniego zachowanie w jeden z dwóch sposobów:<ol><li>Skompiluj ponownie aplikację pod kątem wersji programu .NET Framework starszej niż 4.6. Dla usług hostowanych przez usługi IIS, należy użyć &lt;httpRuntime targetFramework =&quot;x.x&quot;  / &gt; elementu pod kątem starszej wersji programu .NET Framework.</li><li>Dodaj następujący wiersz do <code>&lt;appSettings&gt;</code> sekcji w pliku app.config: <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|


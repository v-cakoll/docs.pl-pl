---
ms.openlocfilehash: 9ec5fa379556dedeaa7a35e34f004340ab47a39c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804566"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Wywołanie CreateDefaultAuthorizationContext z argumentem null został zmieniony

|   |   |
|---|---|
|Szczegóły|Implementacja <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> zwrócone przez wywołanie <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> z null authorizationPolicies argument zmienił jego implementacji w .NET Framework 4.6.|
|Sugestia|W rzadkich przypadkach aplikacje WCF, które używają uwierzytelniania niestandardowego mogą zobaczyć różnice w zachowaniu. W takich przypadkach poprzednie zachowanie można przywrócić na dwa sposoby:<ol><li>Ponownie skompiluj aplikację, aby kierować reklamy na wcześniejszą wersję programu .NET Framework niż 4.6. W przypadku usług hostowanych usługami &lt;IIS użyj&quot;elementu httpRuntime targetFramework= x.x,&quot;  / &gt; aby kierować reklamy na wcześniejszą wersję programu .NET Framework.</li><li>Dodaj następujący wiersz <code>&lt;appSettings&gt;</code> do sekcji pliku app.config:<code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|

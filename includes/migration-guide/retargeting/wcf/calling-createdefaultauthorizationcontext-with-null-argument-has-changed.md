---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615711"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Wywołanie CreateDefaultAuthorizationContext z pustym argumentem zostało zmienione

#### <a name="details"></a>Szczegóły

Implementacja <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> zwracanego przez wywołanie <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> z argumentem authorizationPolicies o wartości null zmieniła swoją implementację w .NET Framework 4,6.

#### <a name="suggestion"></a>Sugestia

W rzadkich przypadkach aplikacje WCF korzystające z uwierzytelniania niestandardowego mogą zobaczyć różnice w zachowaniu. W takich przypadkach poprzednie zachowanie można przywrócić na jeden z dwóch sposobów:

- Skompiluj ponownie aplikację pod kątem wcześniejszej wersji .NET Framework niż 4,6. W przypadku usług hostowanych przez usługi IIS Użyj `<httpRuntime targetFramework="x.x">` elementu jako docelowego dla wcześniejszej wersji .NET Framework.
- Dodaj następujący wiersz do `<appSettings>` sekcji pliku app.config:

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>

---
ms.openlocfilehash: b88f7d4a17f885b687d99ab9410a56039e176080
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614639"
---
### <a name="calls-to-claimsidentity-constructors"></a>Wywołania konstruktorów identyfikator oświadczenia

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4.6.2 istnieje zmiana sposobu, w jaki <xref:System.Security.Claims.ClaimsIdentity> konstruktory z <xref:System.Security.Principal.IIdentity?displayProperty=fullName> parametrem ustawiają <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość. Jeśli <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argument jest <xref:System.Security.Claims.ClaimsIdentity> obiekt i <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość tego <xref:System.Security.Claims.ClaimsIdentity> obiektu nie jest `null` , <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość jest dołączona przy użyciu <xref:System.Security.Claims.ClaimsIdentity.Clone> metody. W Framework 4.6.1 i starszych wersji <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość jest dołączana jako istniejące odwołanie. Ze względu na tę zmianę, rozpoczynając od .NET Framework 4.6.2, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> Właściwość nowego <xref:System.Security.Claims.ClaimsIdentity> obiektu nie jest równa <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=fullName> właściwości <xref:System.Security.Principal.IIdentity?displayProperty=fullName> argumentu konstruktora. W .NET Framework 4.6.1 i starszych wersji jest równa.

#### <a name="suggestion"></a>Sugestia

Jeśli takie zachowanie jest niepożądane, można przywrócić poprzednie zachowanie, ustawiając `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` przełącznik w pliku konfiguracji aplikacji na `true` . Wymaga to dodania następujących `<runtime>` elementów do sekcji pliku web.config:

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />
  </runtime>
</configuration>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})>
- <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)>

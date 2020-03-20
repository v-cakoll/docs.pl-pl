---
ms.openlocfilehash: 6dd7f2a2f6dec306940650beee58104b20788bdb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859275"
---
### <a name="calls-to-claimsidentity-constructors"></a>Wywołania konstrukcji ClaimsIdentity

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.6.2, istnieje <xref:System.Security.Claims.ClaimsIdentity> zmiana w <xref:System.Security.Principal.IIdentity?displayProperty=name> sposób <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> konstruktorów z parametrem ustawić właściwość. Jeśli <xref:System.Security.Principal.IIdentity?displayProperty=name> argument jest <xref:System.Security.Claims.ClaimsIdentity> obiektem, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> a <xref:System.Security.Claims.ClaimsIdentity> właściwość <code>null</code>tego <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> obiektu nie jest , <xref:System.Security.Claims.ClaimsIdentity.Clone> właściwość jest dołączona przy użyciu metody. W framework 4.6.1 i wcześniejszych <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> wersjach właściwość jest dołączona jako istniejące odwołanie. Z <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> powodu tej zmiany, począwszy od .NET Framework 4.6.2, właściwość nowego <xref:System.Security.Claims.ClaimsIdentity> obiektu nie jest równa <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> właściwości argumentu konstruktora. <xref:System.Security.Principal.IIdentity?displayProperty=name> W .NET Framework 4.6.1 i wcześniejszych wersjach jest równa.|
|Sugestia|Jeśli to zachowanie jest niepożądane, można przywrócić <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> poprzednie zachowanie, ustawiając <code>true</code>przełącznik w pliku konfiguracyjnym aplikacji na . Wymaga to dodania do <code>&lt;runtime&gt;</code> sekcji pliku web.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Brzeg|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)?displayProperty=nameWithType></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})?displayProperty=nameWithType></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)?displayProperty=nameWithType></li></ul>|

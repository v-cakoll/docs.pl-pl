---
ms.openlocfilehash: 6dd7f2a2f6dec306940650beee58104b20788bdb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235005"
---
### <a name="calls-to-claimsidentity-constructors"></a>Wywołania ClaimsIdentity konstruktorów

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6.2 nastąpiła zmiana w sposób <xref:System.Security.Claims.ClaimsIdentity> konstruktorów z <xref:System.Security.Principal.IIdentity?displayProperty=name> zestaw parametrów <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> właściwości. Jeśli <xref:System.Security.Principal.IIdentity?displayProperty=name> argument jest <xref:System.Security.Claims.ClaimsIdentity> obiektu i <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> właściwość, która <xref:System.Security.Claims.ClaimsIdentity> obiekt nie jest <code>null</code>, <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> właściwość jest podłączany przy użyciu <xref:System.Security.Claims.ClaimsIdentity.Clone> metody. W ramach 4.6.1 i wcześniejszymi wersjami <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> właściwość jest dołączony jako odwołanie do istniejącego. Ze względu na tę zmianę, począwszy od programu .NET Framework 4.6.2 <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> właściwości nowej <xref:System.Security.Claims.ClaimsIdentity> obiektu nie jest równa <xref:System.Security.Claims.ClaimsIdentity.Actor?displayProperty=name> właściwości konstruktora <xref:System.Security.Principal.IIdentity?displayProperty=name> argumentu. W .NET Framework 4.6.1 i wcześniejszych wersjach jest taki sam.|
|Sugestia|Jeśli to zachowanie jest niepożądany, można przywrócić poprzednie zachowanie przez ustawienie <code>Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity</code> przełącznika w pliku konfiguracji aplikacji w celu <code>true</code>. Wymaga to, że Dodaj następujące polecenie, aby <code>&lt;runtime&gt;</code> sekcji w pliku web.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.6.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity)?displayProperty=nameWithType></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim})?displayProperty=nameWithType></li><li><xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Security.Principal.IIdentity,System.Collections.Generic.IEnumerable{System.Security.Claims.Claim},System.String,System.String,System.String)?displayProperty=nameWithType></li></ul>|

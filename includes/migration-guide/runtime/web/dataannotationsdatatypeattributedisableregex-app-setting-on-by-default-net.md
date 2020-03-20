---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73085538"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>Ustawienie aplikacji "dataAnnotations:dataTypeAttribute:disableRegEx" jest domyślnie włączone w programie .NET Framework 4.7.2

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6.1 wprowadzono<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>ustawienie aplikacji ( ) umożliwiające użytkownikom wyłączenie używania wyrażeń <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>regularnych <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>w atrybutach typu danych (takich jak <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, , i ). Pomaga to zmniejszyć luki w zabezpieczeniach, takie jak unikanie możliwości ataku typu "odmowa usługi" przy użyciu określonych wyrażeń regularnych.<br/>W .NET Framework 4.6.1 to ustawienie aplikacji, aby <code>false</code> wyłączyć użycie programu RegEx został ustawiony domyślnie. Począwszy od programu .NET Framework 4.7.2, <code>true</code> ten przełącznik konfiguracji jest domyślnie ustawiony na dalsze zmniejszenie bezpiecznej luki w zabezpieczeniach dla aplikacji sieci web przeznaczonych dla programu .NET Framework 4.7.2 lub wyższej.|
|Sugestia|Jeśli okaże się, że wyrażenia regularne w aplikacji sieci web nie działają po uaktualnieniu do programu .NET <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> Framework <code>false</code> 4.7.2, można zaktualizować wartość ustawienia, aby powrócić do poprzedniego zachowania.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|

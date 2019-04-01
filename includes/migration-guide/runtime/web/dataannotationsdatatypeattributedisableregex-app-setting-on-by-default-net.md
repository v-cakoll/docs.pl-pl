---
ms.openlocfilehash: 4daa08ce4bbcfe5a7242f19506811e422d0477b7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760744"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>ustawienie aplikacji "dataAnnotations:dataTypeAttribute:disableRegEx" jest domyślnie w programie .NET Framework 4.7.2

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.6.1, ustawienie aplikacji (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) została wprowadzona, umożliwia użytkownikom zablokować używanie wyrażeń regularnych w atrybutach typu danych (takich jak <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, i <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Pozwala to zmniejszyć luki w zabezpieczeniach, takie jak unikanie możliwości ataku typu "odmowa usługi" przy użyciu określonych wyrażeń regularnych.<br/>W programie .NET Framework 4.6.1 ustawiono tego ustawienia aplikacji, aby wyłączyć użycie wyrażenia regularnego <code>false</code> domyślnie. Rozpoczęcie przeczytania artykułu z programem .NET Framework 4.7.2, ta opcja konfiguracji jest równa <code>true</code> domyślnie, aby jeszcze bardziej ograniczyć bezpiecznego luk w zabezpieczeniach dla aplikacji sieci web, których platformą docelową .NET Framework 4.7.2 lub nowszej.|
|Sugestia|Jeśli okaże się, że wyrażeń regularnych w aplikacji sieci web nie działają po uaktualnieniu do wersji .NET Framework 4.7.2, możesz zaktualizować wartość <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> ustawienie <code>false</code> Aby przywrócić poprzednie zachowanie.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appsettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appsettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|


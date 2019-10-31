---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085538"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>ustawienie aplikacji "DataAnnotations: DataTypeAttribute: disableRegEx" jest domyślnie włączone w .NET Framework 4.7.2

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.6.1 wprowadzono ustawienie aplikacji (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>), które umożliwia użytkownikom wyłączenie używania wyrażeń regularnych w atrybutach typu danych (takich jak <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>i <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Dzięki temu można zmniejszyć luki w zabezpieczeniach, takie jak uniknięcie ataku typu "odmowa usługi" przy użyciu określonych wyrażeń regularnych.<br/>W .NET Framework 4.6.1 to ustawienie aplikacji wyłączające użycie wyrażenia regularnego zostało ustawione na domyślnie <code>false</code>. Począwszy od .NET Framework 4.7.2, ten przełącznik konfiguracji jest domyślnie ustawiany na <code>true</code>, aby dodatkowo ograniczyć bezpieczną lukę w zabezpieczeniach aplikacji sieci Web przeznaczonych do .NET Framework 4.7.2 i nowszych.|
|Sugestia|Jeśli okaże się, że wyrażenia regularne w aplikacji sieci Web nie działają po uaktualnieniu do .NET Framework 4.7.2, można zaktualizować wartość ustawienia <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>, aby <code>false</code> przywrócić poprzednie zachowanie.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|

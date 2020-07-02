---
ms.openlocfilehash: f17efc89b738a9fd20cc687de1dae01a44664271
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621238"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>ustawienie aplikacji "DataAnnotations: DataTypeAttribute: disableRegEx" jest domyślnie włączone w .NET Framework 4.7.2

#### <a name="details"></a>Szczegóły

W .NET Framework 4.6.1 wprowadzono ustawienie aplikacji ( <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> ), które umożliwia użytkownikom wyłączenie używania wyrażeń regularnych w atrybutach typu danych (takich jak <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType> , <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> , i <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType> ). Dzięki temu można zmniejszyć luki w zabezpieczeniach, takie jak uniknięcie ataku typu "odmowa usługi" przy użyciu określonych wyrażeń regularnych.<br/>W .NET Framework 4.6.1 to ustawienie aplikacji wyłączające użycie wyrażenia regularnego zostało domyślnie ustawione na wartość <code>false</code> . Począwszy od .NET Framework 4.7.2, ten przełącznik konfiguracji jest domyślnie ustawiany, <code>true</code> Aby dodatkowo ograniczyć bezpieczną lukę w zabezpieczeniach aplikacji sieci Web przeznaczonych .NET Framework 4.7.2 i powyżej.

#### <a name="suggestion"></a>Sugestia

Jeśli okaże się, że wyrażenia regularne w aplikacji sieci Web nie działają po uaktualnieniu do .NET Framework 4.7.2, można zaktualizować wartość <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> Ustawienia, aby <code>false</code> przywrócić poprzednie zachowanie.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|

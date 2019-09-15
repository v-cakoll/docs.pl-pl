---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997683"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Obsługa specjalnej notacji względnych identyfikatorów URI, gdy występuje Unicode

|   |   |
|---|---|
|Szczegóły|<xref:System.Uri>nie będzie już <xref:System.NullReferenceException> zgłaszać w przypadku <xref:System.Uri.TryCreate%2A> wywołania określonych względnych identyfikatorów URI zawierających Unicode. Najprostsza reprodukcja <xref:System.NullReferenceException> znajduje się poniżej, przy czym dwie instrukcje są równoważne:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Aby odtworzyć <xref:System.NullReferenceException>, należy wykonać następujące czynności:<ul><li>Identyfikator URI musi być określony jako względny przez zaczekanie z "http:" i nie jest następujący z "//".</li><li>Identyfikator URI musi zawierać zakodowane w procentach symbole Unicode lub unzastrzeżone.</li></ul>|
|Sugestia|Użytkownicy w zależności od tego zachowania, aby nie zezwalać na względne identyfikatory URI, należy zamiast tego określić <xref:System.UriKind.Absolute?displayProperty=nameWithType> podczas tworzenia identyfikatora URI.|
|Scope|Krawędź|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

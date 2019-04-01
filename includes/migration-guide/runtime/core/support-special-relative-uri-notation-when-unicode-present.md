---
ms.openlocfilehash: c8a6870a9d34889dd8f5305035744bfc63be6af6
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760735"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Obsługa specjalne względną identyfikatora URI notacji gdy obecny jest Unicode

|   |   |
|---|---|
|Szczegóły|<xref:System.Uri> nie będzie już zgłaszać <xref:System.NullReferenceException> podczas wywoływania <xref:System.Uri.TryCreate%2A> na niektórych względne identyfikatory URI zawierający reprodukcja najprostszym Unicode.The <xref:System.NullReferenceException> znajduje się poniżej, przy użyciu dwóch instrukcji równoważne:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Aby odtworzyć <xref:System.NullReferenceException>, następujące elementy muszą być spełnione:<ul><li>Identyfikator URI musi zostać określona jako względna przez dołączenie go z "http:" i postępuj zgodnie z nie "/ /".</li><li>Identyfikator URI musi zawierać procent zakodowane w formacie Unicode lub niezastrzeżone symboli.</li></ul>|
|Sugestia|Użytkowników w zależności od tego zachowania nie zezwala na względne identyfikatory URI zamiast tego należy określić <xref:System.UriKind.Absolute?displayProperty=nameWithType> podczas tworzenia identyfikatora URI.|
|Zakres|Krawędź|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|


---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621181"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Obsługa specjalnej notacji względnych identyfikatorów URI, gdy występuje Unicode

#### <a name="details"></a>Szczegóły

<xref:System.Uri>nie będzie już zgłaszać <xref:System.NullReferenceException> w przypadku wywołania <xref:System.Uri.TryCreate%2A> określonych względnych identyfikatorów URI zawierających Unicode. Najprostsza reprodukcja <xref:System.NullReferenceException> znajduje się poniżej, przy czym dwie instrukcje są równoważne:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Aby odtworzyć <xref:System.NullReferenceException> , należy wykonać następujące czynności:<ul><li>Identyfikator URI musi być określony jako względny przez zaczekanie z "http:" i nie jest następujący z "//".</li><li>Identyfikator URI musi zawierać zakodowane w procentach symbole Unicode lub unzastrzeżone.</li></ul>

#### <a name="suggestion"></a>Sugestia

Użytkownicy w zależności od tego zachowania, aby nie zezwalać na względne identyfikatory URI, należy zamiast tego określić <xref:System.UriKind.Absolute?displayProperty=nameWithType> podczas tworzenia identyfikatora URI.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

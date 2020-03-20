---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997683"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Obsługa specjalnej względnej notacji identyfikatora URI, gdy unicode jest obecny

|   |   |
|---|---|
|Szczegóły|<xref:System.Uri>nie będzie już <xref:System.NullReferenceException> rzucać podczas wywoływania <xref:System.Uri.TryCreate%2A> niektórych względnych identyfikatorów URI zawierających Unicode. Najprostsza reprodukcja znajduje się <xref:System.NullReferenceException> poniżej, przy czym oba stwierdzenia są równoważne:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Aby odtworzyć <xref:System.NullReferenceException>, następujące elementy muszą być prawdziwe:<ul><li>Identyfikator URI musi być określony jako względny, dołączając go do "http:" i nie podążając za nim z '//'.</li><li>Identyfikator URI musi zawierać kod Unicode lub symbole bez zastrzeżeń.</li></ul>|
|Sugestia|Użytkownicy w zależności od tego zachowania, aby nie <xref:System.UriKind.Absolute?displayProperty=nameWithType> zezwalać na względne identyfikatory URI należy określić podczas tworzenia identyfikatora URI.|
|Zakres|Brzeg|
|Wersja|4.7.2|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

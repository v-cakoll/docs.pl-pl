---
ms.openlocfilehash: 3e9a1009167d8a765bc401d64a574bd123736ccd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234026"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Zezwalaj na znaki kontrolne Unicode dwukierunkowe na identyfikatory URI

|   |   |
|---|---|
|Szczegóły|Unicode określa kilka specjalnych znaków sterujących używany do określenia orientacji tekstu. W poprzednich wersjach programu .NET Framework te znaki zostały nieprawidłowo usunięte z wszystkie identyfikatory URI, nawet jeśli były obecne w postaci zakodowane w formacie procent. Aby lepiej wykonaj [RFC 3987](https://tools.ietf.org/html/rfc3987), umożliwiamy teraz te znaki w identyfikatorach URI. Gdy znaleziono Niezakodowane: w identyfikatorze URI, są one zakodowane w formacie procent. Jeśli został wykryty procent, kodowane są pozostawiane jako-to.|
|Sugestia|W przypadku aplikacji przeznaczonych dla wersji programu .NET Framework, począwszy od 4.7.2 Obsługa Unicode znaki dwukierunkowego jest domyślnie włączona. Jeśli ta zmiana jest niepożądany, można ją wyłączyć, dodając następujące [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) przełączyć się do <code>&lt;runtime&gt;</code> sekcję pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>W przypadku aplikacji docelowych z wcześniejszych wersji programu .NET Framework, które działają w wersjach, począwszy od .NET Framework 4.7.2 Obsługa Unicode znaki dwukierunkowego jest domyślnie wyłączona. Możesz je włączyć przez dodanie poniższego [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) przełączyć się do <code>&lt;runtime&gt;</code> części pliku konfiguracyjnego aplikacji::<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.7.2|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

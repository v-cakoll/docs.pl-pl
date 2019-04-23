---
ms.openlocfilehash: f4a5911787fa5f72be1dcd15c67b3f132c3f1110
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804691"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap pomyślnie konwertuje ikon PNG ramek na obiekty mapy bitowej

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji, przeznaczonych dla platformy .NET Framework 4.6 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikon PNG ramki w obiektach mapy bitowej.<p/>W aplikacjach przeznaczonych dla platformy .NET Framework 4.5.2 i wcześniejszymi wersjami <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza wyjątek <xref:System.ArgumentOutOfRangeException> wyjątek, jeśli obiekt ikony ma ramek PNG.<p/>Ta zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem programu .NET Framework 4.6 i implementują specjalna obsługa <xref:System.ArgumentOutOfRangeException> który program jest zgłaszany w przypadku, gdy obiekt ikony ma ramek PNG. Podczas uruchamiania w .NET Framework 4.6, konwersja zakończy się pomyślnie, <xref:System.ArgumentOutOfRangeException> nie jest już zgłaszany, i w związku z tym program obsługi wyjątku nie jest już jest wywoływana.|
|Sugestia|Jeśli to zachowanie jest niepożądany, można zachować poprzednie zachowanie, dodając następujący element do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Jeśli już zawiera plik app.config <code>AppContextSwitchOverrides</code> elementu, nowa wartość powinny zostać scalone z atrybutem wartość następująco:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

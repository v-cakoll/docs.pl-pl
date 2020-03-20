---
ms.openlocfilehash: f4a5911787fa5f72be1dcd15c67b3f132c3f1110
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804568"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap pomyślnie konwertuje ikony z ramkami PNG na obiekty bitmapowe

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji docelowych .NET Framework 4.6, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda pomyślnie konwertuje ikony z ramek PNG do obiektów bitmapowych.<p/>W aplikacjach, które są przeznaczone dla .NET Framework 4.5.2 i wcześniejszych wersji, <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> metoda zgłasza wyjątek, <xref:System.ArgumentOutOfRangeException> jeśli Icon obiekt ma ramki PNG.<p/>Ta zmiana wpływa na aplikacje, które są ponownie kompilowane do celu .NET <xref:System.ArgumentOutOfRangeException> Framework 4.6 i które implementują specjalną obsługę dla tego, który jest generowany, gdy Icon obiekt ma ramki PNG. Po uruchomieniu w ramach .NET Framework 4.6 <xref:System.ArgumentOutOfRangeException> konwersji zakończy się pomyślnie, nie jest już zgłaszany i dlatego program obsługi wyjątków nie jest już wywoływany.|
|Sugestia|Jeśli to zachowanie jest niepożądane, można zachować poprzednie zachowanie, dodając następujący element do <code>&lt;runtime&gt;</code> sekcji pliku app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Jeśli plik app.config zawiera <code>AppContextSwitchOverrides</code> już element, nowa wartość powinna zostać scalona z atrybutem value w ten sposób:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

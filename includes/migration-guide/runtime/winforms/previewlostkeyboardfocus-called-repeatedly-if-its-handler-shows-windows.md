---
ms.openlocfilehash: addfd55fd01b13e9088e4706ff846fc624aafa68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235718"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus jest wywoływana wielokrotnie, jeśli jego obsługa wyświetli okno wiadomości Windows Forms

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5, wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> obsługi spowoduje, że program obsługi, ponowne uruchomienie po zamknięciu okna komunikatu mogłoby spowodować pętlę nieskończoną okien komunikatów.|
|Sugestia|Istnieją dwa sposoby obejścia tego problemu:<ol><li>Można go uniknąć przez wywołanie metody <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType>.</li><li>Może być unikać przez wyświetlanie pola komunikatu z <xref:System.Windows.UIElement.LostKeyboardFocus?displayProperty=nameWithType> programu obsługi zdarzeń (w przeciwieństwie do <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> program obsługi zdarzeń).</li></ol>|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|

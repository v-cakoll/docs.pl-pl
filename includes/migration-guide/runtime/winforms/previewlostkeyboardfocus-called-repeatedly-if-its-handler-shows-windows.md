---
ms.openlocfilehash: 2aa6603e2ed77ffa94fbc6325cd5db50985bda6a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620417"
---
### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus jest wywoływana wielokrotnie, jeśli jej program obsługi wyświetli okno komunikatu Windows Forms

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> z <xref:System.Windows.UIElement.PreviewLostKeyboardFocus> programu obsługi spowoduje ponowne uruchomienie programu obsługi po zamknięciu okna komunikatu, co może spowodować powstanie nieskończonej pętli okien komunikatów.

#### <a name="suggestion"></a>Sugestia

Istnieją dwie opcje obejścia tego problemu:<ol><li>Można to uniknąć, wywołując <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> zamiast <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> .</li><li>Można to uniknąć, wyświetlając okno komunikatu z <xref:System.Windows.UIElement.LostKeyboardFocus> programu obsługi zdarzeń (w przeciwieństwie do <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName> programu obsługi zdarzeń).</li></ol>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|

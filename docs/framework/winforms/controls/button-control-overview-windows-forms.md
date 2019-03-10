---
title: Button — Informacje o formancie (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 505b75d362cea0eddec2b51dc398e2cd8c8d4db8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713397"
---
# <a name="button-control-overview-windows-forms"></a>Button — Informacje o formancie (Formularze systemu Windows)
Formularze Windows <xref:System.Windows.Forms.Button> kontrolki pozwala użytkownikowi na kliknij go, aby wykonać akcję. Po kliknięciu przycisku wygląda, jakby on wypychania i wydania. Zawsze, gdy użytkownik kliknie przycisk <xref:System.Windows.Forms.Control.Click> zostanie wywołana procedura obsługi zdarzeń. Umieść kod w <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń do wykonywania dowolnych akcji wybierzesz.  
  
 Tekst wyświetlany na przycisku znajduje się w <xref:System.Windows.Forms.Control.Text%2A> właściwości. Jeśli tekst jest większa niż szerokość przycisku, wartość będzie zawijany do następnego wiersza. Jednak zostaną przycięte, jeśli formant nie może obsłużyć całkowita wysokość. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie tekstu wyświetlanego przez formant formularzy Windows](how-to-set-the-text-displayed-by-a-windows-forms-control.md). <xref:System.Windows.Forms.Control.Text%2A> Właściwość może zawierać klucz dostępu, który umożliwia użytkownikowi "kliknij" kontrolki, naciskając klawisz ALT, przy użyciu klucza dostępu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md). Wygląd tekstu jest kontrolowany przez <xref:System.Windows.Forms.Control.Font%2A> właściwości i <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> właściwości.  
  
 <xref:System.Windows.Forms.Button> Kontrolki można także wyświetlać obrazy za pomocą <xref:System.Windows.Forms.ButtonBase.Image%2A> i <xref:System.Windows.Forms.ButtonBase.ImageList%2A> właściwości. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie obrazu wyświetlanego przez formant formularzy Windows](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Button>
- [Instrukcje: Odpowiadanie na kliknięcia przycisków formularzy Windows](how-to-respond-to-windows-forms-button-clicks.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Akceptuj przy użyciu narzędzia Projektant](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Instrukcje: Wyznaczanie przycisku Windows Forms na przycisk Anuluj, przy użyciu narzędzia Projektant](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button, kontrolka](button-control-windows-forms.md)

---
title: Informacje o kontrolce przycisku
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 4ba7b333e5414efb4814d64ce50c55e08b27f859
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747074"
---
# <a name="button-control-overview-windows-forms"></a>Button — Informacje o formancie (Formularze systemu Windows)
Kontrolka <xref:System.Windows.Forms.Button> Windows Forms umożliwia użytkownikowi kliknięcie go w celu wykonania akcji. Gdy przycisk zostanie kliknięty, wygląda tak, jakby został wypchnięte i wydzierżawiony. Za każdym razem, gdy użytkownik kliknie przycisk, zostanie wywołana procedura obsługi zdarzeń <xref:System.Windows.Forms.Control.Click>. Aby wykonać dowolną akcję, należy umieścić kod w obsłudze zdarzeń <xref:System.Windows.Forms.Control.Click>.  
  
 Tekst wyświetlany na przycisku jest zawarty we właściwości <xref:System.Windows.Forms.Control.Text%2A>. Jeśli tekst przekracza szerokość przycisku, zostanie zawinięty do następnego wiersza. Jednak zostanie przycięty, Jeśli kontrolka nie będzie mogła obsłużyć jej ogólnej wysokości. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md). Właściwość <xref:System.Windows.Forms.Control.Text%2A> może zawierać klucz dostępu, który umożliwia użytkownikowi "kliknięcie" kontrolki przez naciśnięcie klawisza ALT z klawiszem dostępu. Aby uzyskać szczegółowe informacje, zobacz [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md). Wygląd tekstu jest kontrolowany przez właściwość <xref:System.Windows.Forms.Control.Font%2A> i Właściwość <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>.  
  
 Kontrolka <xref:System.Windows.Forms.Button> może również wyświetlać obrazy przy użyciu właściwości <xref:System.Windows.Forms.ButtonBase.Image%2A> i <xref:System.Windows.Forms.ButtonBase.ImageList%2A>. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie obrazu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Button>
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Sposoby wyboru kontrolki przycisku Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Akceptuj przy użyciu narzędzia Projektant](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Instrukcje: wyznaczanie przycisku Windows Forms na przycisk Anuluj przy użyciu narzędzia Projektant](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button, kontrolka](button-control-windows-forms.md)

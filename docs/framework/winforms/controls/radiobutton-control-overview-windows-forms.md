---
title: RadioButton — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: d07fd4028385dac25ae7413a54f72b331ab91eb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558400"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton — Informacje o formancie [Formularze systemu Windows]
Windows Forms <xref:System.Windows.Forms.RadioButton> formanty wyświetlania zestawu co najmniej dwóch wzajemnie wykluczających się opcji do użytkownika. Chociaż pola wyboru i przyciski opcji może wydawać się działają podobnie, ma jedną istotną różnicą: gdy użytkownik wybierze przycisk radiowy, inne przyciski radiowe w tej samej grupy nie można również wybrać. Z kolei można wybrać dowolną liczbę pól wyboru. Definiowanie Grupa przycisków radiowych informuje użytkownika, "W tym miejscu jest zestaw opcji, z których można wybrać jeden i tylko jeden."  
  
## <a name="using-the-control"></a>Używanie formantu  
 Gdy <xref:System.Windows.Forms.RadioButton> kliknięciu formantu jego <xref:System.Windows.Forms.RadioButton.Checked%2A> właściwość jest ustawiona na `true` i <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń jest wywoływany. <xref:System.Windows.Forms.RadioButton.CheckedChanged> Zdarzenie jest zgłaszane w przypadku wartości <xref:System.Windows.Forms.RadioButton.Checked%2A> zmiany właściwości. Jeśli <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> właściwość jest ustawiona na `true` (ustawienie domyślne), gdy przycisk radiowy zostanie wybrany wszystkich innych użytkowników w grupie są automatycznie czyszczone. Ta właściwość jest zwykle tylko równa `false` kiedy kod sprawdzania poprawności służy do upewnij się, że zaznaczony przycisk radiowy jest opcją dozwolony. Tekst wyświetlany w kontrolce została ustawiona za pomocą <xref:System.Windows.Forms.Control.Text%2A> właściwość, która może zawierać dostępu do skróty klawiaturowe. Klucz dostępu umożliwia użytkownikowi "kliknij" kontrolki, naciskając klawisz ALT, przy użyciu klucza dostępu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) i [jak: Ustawianie tekstu wyświetlanego przez formant formularzy Windows](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 <xref:System.Windows.Forms.RadioButton> Kontroli może znajdować się jak przycisk polecenia wydaje się być wciśnięte, wybranie tej opcji, jeśli <xref:System.Windows.Forms.RadioButton.Appearance%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.Appearance.Button>. Przyciski radiowe można także wyświetlać obrazy za pomocą <xref:System.Windows.Forms.ButtonBase.Image%2A> i <xref:System.Windows.Forms.ButtonBase.ImageList%2A> właściwości. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie obrazu wyświetlanego przez formant formularzy Windows](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.RadioButton>
- [Panel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
- [GroupBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)
- [CheckBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)
- [Instrukcje: Tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)
- [Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Instrukcje: Grupa formantów RadioButton formularzy Windows aby działały jak zestaw](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton, kontrolka](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)

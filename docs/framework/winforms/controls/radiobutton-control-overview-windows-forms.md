---
title: RadioButton, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- RadioButton
helpviewer_keywords:
- RadioButton control [Windows Forms], about RadioButton control
- RadioButton control [Windows Forms], determining state
- radio buttons [Windows Forms], determining state
- radio buttons [Windows Forms], about radio buttons
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
ms.openlocfilehash: bbc93046b69d39caadde4986ff56f067fc206a9e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741138"
---
# <a name="radiobutton-control-overview-windows-forms"></a>RadioButton — Informacje o formancie [Formularze systemu Windows]
Windows Forms <xref:System.Windows.Forms.RadioButton> kontrolki zawierają zestaw dwóch lub kilku wzajemnie wykluczających się opcji dla użytkownika. Chociaż przyciski radiowe i pola wyboru mogą wyglądać podobnie do działania, istnieje ważna różnica: gdy użytkownik wybierze przycisk radiowy, inne przyciski radiowe w tej samej grupie nie mogą być również zaznaczone. W przeciwieństwie można wybrać dowolną liczbę pól wyboru. Zdefiniowanie grupy przycisków radiowych oznacza, że użytkownik jest zestawem opcji, spośród których można wybrać jeden i tylko jeden ".  
  
## <a name="using-the-control"></a>Korzystanie z kontrolki  
 Po kliknięciu kontrolki <xref:System.Windows.Forms.RadioButton> jej Właściwość <xref:System.Windows.Forms.RadioButton.Checked%2A> jest ustawiona na `true` i zostanie wywołana procedura obsługi zdarzeń <xref:System.Windows.Forms.Control.Click>. Zdarzenie <xref:System.Windows.Forms.RadioButton.CheckedChanged> jest zgłaszane, gdy wartość właściwości <xref:System.Windows.Forms.RadioButton.Checked%2A> zostanie zmieniona. Jeśli właściwość <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> jest ustawiona na `true` (wartość domyślna), po wybraniu przycisku radiowego wszystkie pozostałe w grupie są automatycznie wyczyszczone. Ta właściwość jest zazwyczaj ustawiana tylko na `false`, gdy kod weryfikacyjny jest używany, aby upewnić się, że wybrany przycisk radiowy jest dozwolony. Tekst wyświetlany w kontrolce jest ustawiany przy użyciu właściwości <xref:System.Windows.Forms.Control.Text%2A>, która może zawierać skróty klucza dostępu. Klucz dostępu umożliwia użytkownikowi "kliknięcie" kontrolki przez naciśnięcie klawisza ALT z klawiszem dostępu. Aby uzyskać więcej informacji, zobacz [jak: tworzenie klawiszy dostępu dla formantów Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md) i [instrukcje: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 Kontrolka <xref:System.Windows.Forms.RadioButton> może być wyświetlana jak przycisk polecenia, który pojawia się w przypadku wybrania, jeśli jest zaznaczone, jeśli właściwość <xref:System.Windows.Forms.RadioButton.Appearance%2A> jest ustawiona na <xref:System.Windows.Forms.Appearance.Button>. Przyciski radiowe mogą również wyświetlać obrazy przy użyciu właściwości <xref:System.Windows.Forms.ButtonBase.Image%2A> i <xref:System.Windows.Forms.ButtonBase.ImageList%2A>. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Ustawianie obrazu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RadioButton>
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
- [GroupBox, kontrolka — omówienie](groupbox-control-overview-windows-forms.md)
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Instrukcje: grupowanie kontrolek RadioButton formularzy Windows Forms, aby działały jak zestaw](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)
- [RadioButton, kontrolka](radiobutton-control-windows-forms.md)

---
title: 'Instrukcje: Grupa formantów RadioButton formularzy Windows aby działały jak zestaw'
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 2d0f32c506025c2d7f302bca67aa20e24d71a865
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723299"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Instrukcje: Grupa formantów RadioButton formularzy Windows aby działały jak zestaw
Windows Forms <xref:System.Windows.Forms.RadioButton> formanty są przeznaczone do zapewniają użytkownikom wybór spośród dwóch lub więcej ustawień, których można przypisać tylko jedną procedury lub obiektu. Na przykład grupy <xref:System.Windows.Forms.RadioButton> formanty mogą być wyświetlane wybór przewoźników pakietu dla zamówienia, ale tylko jeden przewoźników będzie używany. W związku z tym tylko jeden <xref:System.Windows.Forms.RadioButton> w danym momencie może być zaznaczony, nawet jeśli jest częścią grupy funkcjonalnej.  
  
 Grupowanie przycisków radiowych za pomocą rysowania w kontenerze takich jak <xref:System.Windows.Forms.Panel> kontroli <xref:System.Windows.Forms.GroupBox> , formularz lub formant. Wszystkie przyciski radiowe, które są dodawane bezpośrednio do formularza stają się z jednej grupy. Aby dodać osobnych grup, trzeba je umieścić wewnątrz paneli lub pola grupy. Aby uzyskać więcej informacji na temat paneli lub pola grupy zobacz [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md) lub [— informacje o formancie GroupBox](groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Do grupy kontrolek RadioButton jako zestaw funkcji, niezależnie od innych zestawów  
  
1.  Przeciągnij <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel> z kontrolować **Windows Forms** karcie **przybornika** na formularz.  
  
2.  Rysowanie <xref:System.Windows.Forms.RadioButton> formantów na <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel> kontroli.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.RadioButton>
- [RadioButton, kontrolka — omówienie](radiobutton-control-overview-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
- [GroupBox, kontrolka — omówienie](groupbox-control-overview-windows-forms.md)
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [RadioButton, kontrolka](radiobutton-control-windows-forms.md)

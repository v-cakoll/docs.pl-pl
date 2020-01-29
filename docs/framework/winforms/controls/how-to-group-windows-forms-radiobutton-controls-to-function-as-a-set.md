---
title: Grupowanie kontrolek RadioButton do działania jako zestaw
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: c4b37c84bf0f93837b91c743c7681d39fd83a659
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732951"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Porady: grupowanie formantów RadioButton formularzy systemu Windows, aby działały jak zestaw
Windows Forms <xref:System.Windows.Forms.RadioButton> kontrolek umożliwiają użytkownikom wybór spośród dwóch lub więcej ustawień, do których można przypisać tylko jeden z nich do procedury lub obiektu. Na przykład grupa formantów <xref:System.Windows.Forms.RadioButton> może wyświetlić wybór przewoźników pakietów dla zamówienia, ale tylko jeden z nich będzie używany. W związku z tym można wybrać tylko jedną <xref:System.Windows.Forms.RadioButton> w danym momencie, nawet jeśli jest to część grupy funkcjonalnej.  
  
 Przyciski radiowe są grupowane przez rysowanie ich wewnątrz kontenera, takiego jak kontrolka <xref:System.Windows.Forms.Panel>, kontrolka <xref:System.Windows.Forms.GroupBox> lub formularz. Wszystkie przyciski radiowe dodawane bezpośrednio do formularza stają się jedną grupą. Aby dodać oddzielne grupy, należy umieścić je wewnątrz paneli lub grup pól. Aby uzyskać więcej informacji na temat paneli lub grup, zobacz [Omówienie kontrolki panel](panel-control-overview-windows-forms.md) lub [kontrolka widoku grupy](groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Aby zgrupować kontrolki RadioButton jako zestaw do działania niezależnie od innych zestawów  
  
1. Przeciągnij formant <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel> z karty **Windows Forms** w **przyborniku** na formularz.  
  
2. Rysuj <xref:System.Windows.Forms.RadioButton> kontrolki w kontrolce <xref:System.Windows.Forms.GroupBox> lub <xref:System.Windows.Forms.Panel>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RadioButton>
- [RadioButton, kontrolka — omówienie](radiobutton-control-overview-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
- [GroupBox, kontrolka — omówienie](groupbox-control-overview-windows-forms.md)
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [RadioButton, kontrolka](radiobutton-control-windows-forms.md)

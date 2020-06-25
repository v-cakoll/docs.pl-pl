---
title: Grupowanie kontrolek RadioButton do działania jako zestaw
description: Dowiedz się, jak grupować Windows Forms formantów RadioButton, aby funkcjonowały niezależnie od innych zestawów.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325922"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Porady: grupowanie formantów RadioButton formularzy systemu Windows, aby działały jak zestaw
<xref:System.Windows.Forms.RadioButton>Kontrolki Windows Forms zaprojektowano w celu zapewnienia użytkownikom wyboru spośród dwóch lub więcej ustawień, do których można przypisać tylko jeden element do procedury lub obiektu. Na przykład grupa <xref:System.Windows.Forms.RadioButton> kontrolek może wyświetlić wybór przewoźników pakietów dla zamówienia, ale tylko jeden z nich będzie używany. W związku z tym można wybrać tylko jedną z nich <xref:System.Windows.Forms.RadioButton> naraz, nawet jeśli jest to część grupy funkcjonalnej.  
  
 Możesz grupować przyciski radiowe, rysując je wewnątrz kontenera, takiego jak <xref:System.Windows.Forms.Panel> kontrolka, <xref:System.Windows.Forms.GroupBox> kontrolka lub formularz. Wszystkie przyciski radiowe dodawane bezpośrednio do formularza stają się jedną grupą. Aby dodać oddzielne grupy, należy umieścić je wewnątrz paneli lub grup pól. Aby uzyskać więcej informacji na temat paneli lub grup, zobacz [Omówienie kontrolki panel](panel-control-overview-windows-forms.md) lub [kontrolka widoku grupy](groupbox-control-overview-windows-forms.md).  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Aby zgrupować kontrolki RadioButton jako zestaw do działania niezależnie od innych zestawów  
  
1. Przeciągnij <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> kontrolkę lub z karty **Windows Forms** w **przyborniku** na formularz.  
  
2. Rysuj <xref:System.Windows.Forms.RadioButton> kontrolki w <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> kontrolce lub.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.RadioButton>
- [RadioButton, kontrolka — omówienie](radiobutton-control-overview-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
- [GroupBox — Informacje o formancie](groupbox-control-overview-windows-forms.md)
- [CheckBox, kontrolka — omówienie](checkbox-control-overview-windows-forms.md)
- [RadioButton, kontrolka](radiobutton-control-windows-forms.md)

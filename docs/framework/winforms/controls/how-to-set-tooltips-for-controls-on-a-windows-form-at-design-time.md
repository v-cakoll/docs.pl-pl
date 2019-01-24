---
title: 'Instrukcje: Ustawienie elementu ToolTips dla formantów w formularzu Windows w czasie projektowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: ebefe596728b5cabd9d24720d8c39f13c8836bd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609411"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Instrukcje: Ustawienie elementu ToolTips dla formantów w formularzu Windows w czasie projektowania
Możesz ustawić <xref:System.Windows.Forms.ToolTip> ciągu w kodzie lub w programie Windows Forms Designer. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.ToolTip> składników, zobacz [— informacje o składniku ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-a-tooltip-programmatically"></a>Aby programowo ustawić etykietkę narzędzia  
  
1.  Dodaj kontrolkę która będzie wyświetlana etykietka narzędzia.  
  
2.  Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a>Aby ustawić etykietkę narzędzi w Projektancie  
  
1.  Dodaj <xref:System.Windows.Forms.ToolTip> składnika do formularza.  
  
2.  Wybierz kontrolkę która będzie wyświetlić wskazówkę, albo dodaj go do formularza.  
  
3.  W **właściwości** oknie **etykietki narzędzia w ToolTip1** wartość na odpowiedni ciąg tekstowy.  

### <a name="to-remove-a-tooltip-programmatically"></a>Aby usunąć etykietka narzędzia programistyczne  
  
1.  Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.  
  
    ```vb  
    ' In this example, Button1 is the control displaying the ToolTip.  
    ToolTip1.SetToolTip(Button1, Nothing)  
    ```  
  
    ```csharp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1.SetToolTip(button1, null);  
    ```  
  
    ```cpp  
    // In this example, button1 is the control displaying the ToolTip.  
    toolTip1->SetToolTip(button1, NULL);  
    ```  
  
### <a name="to-remove-a-tooltip-in-the-designer"></a>Aby usunąć etykietki narzędzia w Projektancie  
  
1.  Wybierz kontrolkę która jest wyświetlana etykietka narzędzia.  
  
2.  W **właściwości** oknie Usuwanie tekstu z **etykietki narzędzia w ToolTip1**.  

## <a name="see-also"></a>Zobacz także
- [ToolTip, składnik — omówienie](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)
- [Instrukcje: Zmienianie opóźnienia składnika ToolTip formularzy Windows](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip, składnik](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)

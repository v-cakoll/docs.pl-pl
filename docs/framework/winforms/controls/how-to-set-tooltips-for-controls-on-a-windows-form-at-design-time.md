---
title: 'Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 4e4623c1c0fe7d082e4d1a1f404ddaa94e79fc2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533633"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania
Można ustawić <xref:System.Windows.Forms.ToolTip> ciągu w kodzie, lub w narzędziu Projektant dla formularzy systemu Windows. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.ToolTip> składników, zobacz [informacje o składniku ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-a-tooltip-programmatically"></a>Aby ustawić programowo etykietka narzędzia  
  
1.  Dodaj kontrolkę, która będzie wyświetlana etykietka narzędzia.  
  
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
  
### <a name="to-set-a-tooltip-in-the-designer"></a>Aby ustawić etykietka narzędzia w Projektancie  
  
1.  Dodaj <xref:System.Windows.Forms.ToolTip> składnika w formularzu.  
  
2.  Wybierz kontrolkę, która będzie wyświetlenia wskazówki lub dodanie go do formularza.  
  
3.  W **właściwości** ustaw **etykietki narzędzia w ToolTip1** wartość na odpowiedni ciąg tekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [ToolTip, składnik — omówienie](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [ToolTip, składnik](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)

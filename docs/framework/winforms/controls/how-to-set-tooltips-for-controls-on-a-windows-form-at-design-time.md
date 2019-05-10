---
title: 'Instrukcje: ustawienie elementu ToolTips dla kontrolek w formularzu systemu Windows w czasie projektowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211684"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Instrukcje: Ustawienie elementu ToolTips dla formantów w formularzu Windows w czasie projektowania

Możesz ustawić <xref:System.Windows.Forms.ToolTip> ciągu w kodzie lub w programie Windows Forms Designer w programie Visual Studio. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.ToolTip> składników, zobacz [— informacje o składniku ToolTip](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Programowe Ustawianie etykietki narzędzia

1. Dodaj kontrolkę która będzie wyświetlana etykietka narzędzia.

2. Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.

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

## <a name="set-a-tooltip-in-the-designer"></a>Ustawić etykietkę narzędzi w Projektancie

1. W programie Visual Studio, należy dodać <xref:System.Windows.Forms.ToolTip> składnika do formularza.

2. Wybierz kontrolkę która będzie wyświetlić wskazówkę, albo dodaj go do formularza.

3. W **właściwości** oknie **etykietki narzędzia w ToolTip1** wartość na odpowiedni ciąg tekstowy.

### <a name="to-remove-a-tooltip-programmatically"></a>Aby usunąć etykietka narzędzia programistyczne

1. Użyj <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metody <xref:System.Windows.Forms.ToolTip> składnika.

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

## <a name="remove-a-tooltip-in-the-designer"></a>Usuń etykietkę narzędzia w Projektancie

1. W programie Visual Studio wybierz kontrolkę która jest wyświetlana etykietka narzędzia.

2. W **właściwości** oknie Usuwanie tekstu z **etykietki narzędzia w ToolTip1**.

## <a name="see-also"></a>Zobacz także

- [ToolTip, składnik — omówienie](tooltip-component-overview-windows-forms.md)
- [Instrukcje: Zmienianie opóźnienia składnika ToolTip formularzy Windows](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip, składnik](tooltip-component-windows-forms.md)

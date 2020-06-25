---
title: 'Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania'
description: Dowiedz się, jak ustawić etykietki narzędzi dla formantów programowo lub w Projektant formularzy systemu Windows w programie Visual Studio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325972"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Porady: Ustawianie etykietek narzędzi dla kontrolek w formularzu systemu Windows w czasie projektowania

Można ustawić <xref:System.Windows.Forms.ToolTip> ciąg w kodzie lub w Projektant formularzy systemu Windows w programie Visual Studio. Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.ToolTip> składnika, zobacz [Omówienie składnika etykietki narzędzia](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Programistyczne Ustawianie etykietki narzędzia

1. Dodaj kontrolkę, która będzie wyświetlać etykietkę narzędzia.

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

## <a name="set-a-tooltip-in-the-designer"></a>Ustawianie etykietki narzędzia w projektancie

1. W programie Visual Studio Dodaj <xref:System.Windows.Forms.ToolTip> składnik do formularza.

2. Wybierz kontrolkę, która będzie wyświetlać etykietkę narzędzia, lub Dodaj ją do formularza.

3. W oknie **Właściwości** Ustaw **etykietkę narzędzia dla wartości ToolTip1** na odpowiedni ciąg tekstowy.

### <a name="to-remove-a-tooltip-programmatically"></a>Aby programowo usunąć etykietkę narzędzia

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

## <a name="remove-a-tooltip-in-the-designer"></a>Usuwanie etykietki narzędzia w projektancie

1. W programie Visual Studio Wybierz kontrolkę wyświetlającą etykietkę narzędzia.

2. W oknie **Właściwości** Usuń tekst w **etykietce narzędzia ToolTip1**.

## <a name="see-also"></a>Zobacz też

- [ToolTip — Informacje o składniku](tooltip-component-overview-windows-forms.md)
- [Instrukcje: zmienianie opóźnienia składnika ToolTip formularzy Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip, składnik](tooltip-component-windows-forms.md)

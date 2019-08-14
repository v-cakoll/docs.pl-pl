---
title: 'Instrukcje: tworzenie przycisków przełączania w kontrolkach ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972355"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Instrukcje: tworzenie przycisków przełączania w kontrolkach ToolStrip

Gdy użytkownik kliknie przycisk przełączania, wydaje się wklęsły i zachowuje wklęsły wygląd do momentu ponownego kliknięcia przycisku przez użytkownika.

## <a name="to-create-a-toggling-toolstripbutton"></a>Aby utworzyć element ToolStripButton przełączenia

- Użyj kodu, takiego jak Poniższy przykład kodu. Ten kod zakłada, że formularz <xref:System.Windows.Forms.ToolStrip> zawiera kontrolkę i że jej <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekcja zawiera <xref:System.Windows.Forms.ToolStripButton> nazwę `toolStripButton1`. Zakłada również, że istnieje procedura obsługi zdarzeń wywołana `toolStripButton1_CheckedChanged`.

    ```vb
    toolStripButton1.CheckOnClick = True
    toolStripButton1.CheckedChanged AddressOf _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

    ```csharp
    toolStripButton1.CheckOnClick = true;
    toolStripButton1.CheckedChanged += new _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripButton>
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)

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
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="436c0-102">Instrukcje: tworzenie przycisków przełączania w kontrolkach ToolStrip</span><span class="sxs-lookup"><span data-stu-id="436c0-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>

<span data-ttu-id="436c0-103">Gdy użytkownik kliknie przycisk przełączania, wydaje się wklęsły i zachowuje wklęsły wygląd do momentu ponownego kliknięcia przycisku przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="436c0-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>

## <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="436c0-104">Aby utworzyć element ToolStripButton przełączenia</span><span class="sxs-lookup"><span data-stu-id="436c0-104">To create a toggling ToolStripButton</span></span>

- <span data-ttu-id="436c0-105">Użyj kodu, takiego jak Poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="436c0-105">Use code such as the following code example.</span></span> <span data-ttu-id="436c0-106">Ten kod zakłada, że formularz <xref:System.Windows.Forms.ToolStrip> zawiera kontrolkę i że jej <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekcja zawiera <xref:System.Windows.Forms.ToolStripButton> nazwę `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="436c0-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="436c0-107">Zakłada również, że istnieje procedura obsługi zdarzeń wywołana `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="436c0-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="436c0-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="436c0-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="436c0-109">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="436c0-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)

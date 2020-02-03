---
title: Obiekty układu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1615b9c4df222edd95cda9bceae622ba6f1d8d78
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736340"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="4ee86-102">Instrukcje: obiekty warstwy na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ee86-102">How to: Layer objects on Windows Forms</span></span>

<span data-ttu-id="4ee86-103">Podczas tworzenia złożonego interfejsu użytkownika lub pracy z formularzem interfejsu wielu dokumentów (MDI), często zajdzie potrzeba warstwy formantów i formularzy podrzędnych, aby utworzyć bardziej złożone interfejsy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4ee86-103">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="4ee86-104">Aby przenieść i śledzić kontrolki i okna w kontekście grupy, można manipulować ich *kolejnością z*.</span><span class="sxs-lookup"><span data-stu-id="4ee86-104">To move and keep track of controls and windows within the context of a group, you manipulate their *z-order*.</span></span> <span data-ttu-id="4ee86-105">Porządek osi z jest wizualną warstwą formantów w formularzu wzdłuż osi z (głębokości) formularza.</span><span class="sxs-lookup"><span data-stu-id="4ee86-105">Z-order is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="4ee86-106">Okno w górnej części porządku osi z nakładają się na wszystkie inne okna.</span><span class="sxs-lookup"><span data-stu-id="4ee86-106">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="4ee86-107">Wszystkie inne okna nakładają się na okno w dolnej części porządku osi z.</span><span class="sxs-lookup"><span data-stu-id="4ee86-107">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="4ee86-108">Do kontrolek warstwy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="4ee86-108">To layer controls at design time</span></span>

1. <span data-ttu-id="4ee86-109">W programie Visual Studio Wybierz kontrolkę, którą chcesz przydzielyć do warstwy.</span><span class="sxs-lookup"><span data-stu-id="4ee86-109">In Visual Studio, select a control that you want to layer.</span></span>

2. <span data-ttu-id="4ee86-110">W menu **Format** wybierz pozycję **Zamówienie**, a następnie wybierz pozycję **Przesuń na wierzch** lub **Przesuń na spód**.</span><span class="sxs-lookup"><span data-stu-id="4ee86-110">On the **Format** menu, select **Order**, and then select **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="4ee86-111">Na programistyczne kontrolki warstwy</span><span class="sxs-lookup"><span data-stu-id="4ee86-111">To layer controls programmatically</span></span>

<span data-ttu-id="4ee86-112">Użyj metod <xref:System.Windows.Forms.Control.BringToFront%2A> i <xref:System.Windows.Forms.Control.SendToBack%2A> do manipulowania kolejnością z kontrolek z.</span><span class="sxs-lookup"><span data-stu-id="4ee86-112">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

<span data-ttu-id="4ee86-113">Na przykład, jeśli formant <xref:System.Windows.Forms.TextBox>, `txtFirstName`, znajduje się pod inną kontrolką i chcesz go umieścić na górze, użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="4ee86-113">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

```vb
txtFirstName.BringToFront()
```

```csharp
txtFirstName.BringToFront();
```

```cpp
txtFirstName->BringToFront();
```

> [!NOTE]
> <span data-ttu-id="4ee86-114">Windows Forms obsługuje *zawieranie kontrolek*.</span><span class="sxs-lookup"><span data-stu-id="4ee86-114">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="4ee86-115">Zawieranie kontrolek obejmuje umieszczenie wielu kontrolek w obrębie zawierającej kontrolki, takich jak liczba formantów <xref:System.Windows.Forms.RadioButton> w kontrolce <xref:System.Windows.Forms.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="4ee86-115">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="4ee86-116">Następnie można przyciągać warstwy do kontrolek zawierających.</span><span class="sxs-lookup"><span data-stu-id="4ee86-116">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="4ee86-117">Przeniesienie pola grupy przenosi również kontrolki, ponieważ znajdują się w nim.</span><span class="sxs-lookup"><span data-stu-id="4ee86-117">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ee86-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ee86-118">See also</span></span>

- [<span data-ttu-id="4ee86-119">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ee86-119">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="4ee86-120">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="4ee86-120">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="4ee86-121">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ee86-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="4ee86-122">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="4ee86-122">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)

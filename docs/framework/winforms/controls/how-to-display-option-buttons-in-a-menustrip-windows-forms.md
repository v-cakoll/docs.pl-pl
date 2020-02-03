---
title: 'Porady: wyświetlanie przycisków opcji w formancie MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735526"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="6daa5-102">Porady: wyświetlanie przycisków opcji w formancie MenuStrip (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="6daa5-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>

<span data-ttu-id="6daa5-103">Przyciski opcji, znane także jako przyciski radiowe, są podobne do pól wyboru, z wyjątkiem tego, że użytkownicy mogą wybrać tylko jedną naraz.</span><span class="sxs-lookup"><span data-stu-id="6daa5-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="6daa5-104">Chociaż domyślnie Klasa <xref:System.Windows.Forms.ToolStripMenuItem> nie zapewnia zachowania przycisku opcji, klasa zapewnia zachowanie w przypadku pola wyboru, które można dostosować, aby zaimplementować zachowanie przycisku opcji dla elementów menu w kontrolce <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6daa5-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="6daa5-105">Gdy właściwość <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> elementu menu jest `true`, użytkownicy mogą kliknąć element, aby włączyć wyświetlanie znacznika wyboru.</span><span class="sxs-lookup"><span data-stu-id="6daa5-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="6daa5-106">Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> wskazuje bieżący stan elementu.</span><span class="sxs-lookup"><span data-stu-id="6daa5-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="6daa5-107">Aby zaimplementować podstawowe zachowanie przycisku opcji, należy się upewnić, że po wybraniu elementu właściwość <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> dla poprzednio wybranego elementu ma być `false`.</span><span class="sxs-lookup"><span data-stu-id="6daa5-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>

<span data-ttu-id="6daa5-108">W poniższych procedurach opisano sposób implementacji tej i dodatkowych funkcji w klasie, która dziedziczy klasę <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="6daa5-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="6daa5-109">Klasa `ToolStripRadioButtonMenuItem` przesłania składowe, takie jak <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> i <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>, aby zapewnić zachowanie wyboru i wygląd przycisków opcji.</span><span class="sxs-lookup"><span data-stu-id="6daa5-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="6daa5-110">Ponadto ta klasa przesłania Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>, dzięki czemu opcje w podmenu są wyłączone, chyba że jest zaznaczony element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="6daa5-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>

## <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="6daa5-111">Aby zaimplementować zachowanie wyboru przycisku opcji</span><span class="sxs-lookup"><span data-stu-id="6daa5-111">To implement option-button selection behavior</span></span>

1. <span data-ttu-id="6daa5-112">Zainicjuj Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>, aby `true` w celu włączenia wyboru elementu.</span><span class="sxs-lookup"><span data-stu-id="6daa5-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <span data-ttu-id="6daa5-113">Zastąp metodę <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A>, aby wyczyścić zaznaczenie poprzednio wybranego elementu po zaznaczeniu nowego elementu.</span><span class="sxs-lookup"><span data-stu-id="6daa5-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <span data-ttu-id="6daa5-114">Zastąp metodę <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A>, aby upewnić się, że kliknięcie elementu, który został już wybrany, nie spowoduje usunięcia zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="6daa5-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="6daa5-115">Aby zmodyfikować wygląd elementów przycisku opcji</span><span class="sxs-lookup"><span data-stu-id="6daa5-115">To modify the appearance of the option-button items</span></span>

1. <span data-ttu-id="6daa5-116">Zastąp metodę <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>, aby zastąpić domyślny znacznik wyboru z przyciskiem opcji za pomocą klasy <xref:System.Windows.Forms.RadioButtonRenderer>.</span><span class="sxs-lookup"><span data-stu-id="6daa5-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <span data-ttu-id="6daa5-117">Przesłoń metody <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>i <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A>, aby śledzić stan myszy i upewnić się, że metoda <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> maluje poprawny stan przycisku opcji.</span><span class="sxs-lookup"><span data-stu-id="6daa5-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="6daa5-118">Aby wyłączyć opcje w podmenu, gdy element nadrzędny nie jest zaznaczony</span><span class="sxs-lookup"><span data-stu-id="6daa5-118">To disable options on a submenu when the parent item is not selected</span></span>

1. <span data-ttu-id="6daa5-119">Zastąp Właściwość <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> tak, aby element był wyłączony, gdy ma element nadrzędny z <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> wartością `true` i <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="6daa5-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <span data-ttu-id="6daa5-120">Zastąp metodę <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A>, aby subskrybować zdarzenie <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6daa5-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. <span data-ttu-id="6daa5-121">W obsłudze zdarzenia <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> elementu nadrzędnego należy unieważnić element w celu zaktualizowania wyświetlania z nowym włączonym stanem.</span><span class="sxs-lookup"><span data-stu-id="6daa5-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a><span data-ttu-id="6daa5-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="6daa5-122">Example</span></span>

<span data-ttu-id="6daa5-123">Poniższy przykład kodu zawiera kompletną klasę `ToolStripRadioButtonMenuItem`, a Klasa <xref:System.Windows.Forms.Form> i Klasa `Program` do zademonstrowania zachowania przycisku opcji.</span><span class="sxs-lookup"><span data-stu-id="6daa5-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a><span data-ttu-id="6daa5-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6daa5-124">Compiling the Code</span></span>

<span data-ttu-id="6daa5-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6daa5-125">This example requires:</span></span>

- <span data-ttu-id="6daa5-126">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="6daa5-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="6daa5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6daa5-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="6daa5-128">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6daa5-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="6daa5-129">Instrukcje: implementowanie niestandardowego elementu ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="6daa5-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)

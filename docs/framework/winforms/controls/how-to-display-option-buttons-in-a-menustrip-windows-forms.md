---
title: 'Instrukcje: Wyświetlanie przycisków opcji w elemencie MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: 94d683369edd6583ad8b01c2ce3f393567a5ed75
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971928"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="c21eb-102">Instrukcje: Wyświetlanie przycisków opcji w elemencie MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c21eb-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>

<span data-ttu-id="c21eb-103">Przyciski opcji, znane także jako przyciski radiowe, są podobne do pól wyboru, z wyjątkiem tego, że użytkownicy mogą wybrać tylko jedną naraz.</span><span class="sxs-lookup"><span data-stu-id="c21eb-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="c21eb-104">Mimo że domyślnie <xref:System.Windows.Forms.ToolStripMenuItem> Klasa nie zapewnia zachowania przycisku opcji, klasa zapewnia zachowanie w przypadku pola wyboru, które można dostosować, aby zaimplementować zachowanie przycisku opcji dla elementów menu <xref:System.Windows.Forms.MenuStrip> w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="c21eb-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="c21eb-105">Gdy właściwość elementu menu jest `true`, użytkownicy mogą kliknąć element, aby włączyć wyświetlanie znacznika wyboru. <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A></span><span class="sxs-lookup"><span data-stu-id="c21eb-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="c21eb-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Właściwość wskazuje bieżący stan elementu.</span><span class="sxs-lookup"><span data-stu-id="c21eb-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="c21eb-107">Aby zaimplementować podstawowe zachowanie przycisku opcji, należy się upewnić, że po wybraniu elementu <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość dla poprzednio wybranego elementu zostanie ustawiona na `false`wartość.</span><span class="sxs-lookup"><span data-stu-id="c21eb-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>

<span data-ttu-id="c21eb-108">Poniższe procedury opisują sposób wdrażania tej i dodatkowych funkcji w klasie, która dziedziczy <xref:System.Windows.Forms.ToolStripMenuItem> klasę.</span><span class="sxs-lookup"><span data-stu-id="c21eb-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="c21eb-109">Klasa przesłania składowe, takie <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> jak <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> i, aby zapewnić zachowanie wyboru i wygląd przycisków opcji. `ToolStripRadioButtonMenuItem`</span><span class="sxs-lookup"><span data-stu-id="c21eb-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="c21eb-110">Ponadto ta klasa przesłania <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość, dzięki czemu opcje w podmenu są wyłączone, chyba że element nadrzędny jest zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="c21eb-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>

## <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="c21eb-111">Aby zaimplementować zachowanie wyboru przycisku opcji</span><span class="sxs-lookup"><span data-stu-id="c21eb-111">To implement option-button selection behavior</span></span>

1. <span data-ttu-id="c21eb-112">`true` Zainicjuj <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość, aby włączyć wybór elementu.</span><span class="sxs-lookup"><span data-stu-id="c21eb-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <span data-ttu-id="c21eb-113">Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metodę, aby wyczyścić zaznaczenie poprzednio wybranego elementu po zaznaczeniu nowego elementu.</span><span class="sxs-lookup"><span data-stu-id="c21eb-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <span data-ttu-id="c21eb-114">Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodę, aby upewnić się, że kliknięcie elementu, który został już wybrany, nie spowoduje usunięcia zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="c21eb-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="c21eb-115">Aby zmodyfikować wygląd elementów przycisku opcji</span><span class="sxs-lookup"><span data-stu-id="c21eb-115">To modify the appearance of the option-button items</span></span>

1. <span data-ttu-id="c21eb-116">Zastąp <xref:System.Windows.Forms.RadioButtonRenderer> metodę, aby zastąpić domyślny znacznik wyboru z przyciskiem opcji za pomocą klasy. <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="c21eb-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <span data-ttu-id="c21eb-117"><xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A> Zastąp<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>metody ,,<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> i ,<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> aby śledzić stan myszy i upewnij się, że metoda maluje poprawny stan przycisku opcji. <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A></span><span class="sxs-lookup"><span data-stu-id="c21eb-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="c21eb-118">Aby wyłączyć opcje w podmenu, gdy element nadrzędny nie jest zaznaczony</span><span class="sxs-lookup"><span data-stu-id="c21eb-118">To disable options on a submenu when the parent item is not selected</span></span>

1. <span data-ttu-id="c21eb-119">`false` <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> `true` <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> Zastąp Właściwośćtak,abyelementbyłwyłączony,gdymaelementnadrzędnyzjednocześniewartościąiwartością.<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A></span><span class="sxs-lookup"><span data-stu-id="c21eb-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <span data-ttu-id="c21eb-120"><xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metodę, aby subskrybować zdarzenie elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c21eb-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. <span data-ttu-id="c21eb-121">W programie obsługi zdarzenia elementu <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> nadrzędnego Unieważnij element w celu zaktualizowania wyświetlania przy użyciu nowego włączonego stanu.</span><span class="sxs-lookup"><span data-stu-id="c21eb-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a><span data-ttu-id="c21eb-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="c21eb-122">Example</span></span>

<span data-ttu-id="c21eb-123">Poniższy przykład kodu zawiera kompletną `ToolStripRadioButtonMenuItem` klasę <xref:System.Windows.Forms.Form> oraz klasę i `Program` klasę, aby pokazać zachowanie przycisku opcji.</span><span class="sxs-lookup"><span data-stu-id="c21eb-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a><span data-ttu-id="c21eb-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c21eb-124">Compiling the Code</span></span>

<span data-ttu-id="c21eb-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c21eb-125">This example requires:</span></span>

- <span data-ttu-id="c21eb-126">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="c21eb-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="c21eb-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c21eb-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="c21eb-128">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c21eb-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="c21eb-129">Instrukcje: Implementowanie niestandardowego elementu ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="c21eb-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)

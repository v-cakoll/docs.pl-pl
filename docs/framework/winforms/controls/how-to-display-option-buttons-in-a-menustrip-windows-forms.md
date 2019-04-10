---
title: 'Instrukcje: Wyświetlanie przycisków opcji w formancie MenuStrip (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: e764c7e181870d8faf6157cacc13164977ce2e3b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306238"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="eaf86-102">Instrukcje: Wyświetlanie przycisków opcji w formancie MenuStrip (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="eaf86-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="eaf86-103">Przyciski opcji, znany także jako przyciski radiowe są podobne do pola wyboru, z tą różnicą, że użytkownicy mogą wybrać tylko jedną na raz.</span><span class="sxs-lookup"><span data-stu-id="eaf86-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="eaf86-104">Mimo że domyślnie <xref:System.Windows.Forms.ToolStripMenuItem> klasa nie zapewnia zachowanie przycisku opcji, klasa zapewnia zachowanie pola wyboru, które można dostosować, aby zaimplementować zachowanie przycisku opcji elementów menu w <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="eaf86-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="eaf86-105">Gdy <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość elementu menu jest `true`, użytkownicy będą mogli kliknąć element, aby przełączać wyświetlanie znacznik wyboru.</span><span class="sxs-lookup"><span data-stu-id="eaf86-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="eaf86-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Właściwość wskazuje bieżący stan elementu.</span><span class="sxs-lookup"><span data-stu-id="eaf86-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="eaf86-107">Aby zaimplementować zachowanie podstawowe przycisk opcji, należy upewnić się, jeśli element jest wybrany, można skonfigurować ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość poprzednio wybranego elementu do `false`.</span><span class="sxs-lookup"><span data-stu-id="eaf86-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="eaf86-108">W poniższych procedurach opisano sposób implementacji i skorzystać z dodatkowych funkcji w klasie, która dziedziczy <xref:System.Windows.Forms.ToolStripMenuItem> klasy.</span><span class="sxs-lookup"><span data-stu-id="eaf86-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="eaf86-109">`ToolStripRadioButtonMenuItem` Klasa zastępuje elementy członkowskie <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> i <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> zachowanie podczas zaznaczania i wygląd przycisków opcji.</span><span class="sxs-lookup"><span data-stu-id="eaf86-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="eaf86-110">Ponadto ta klasa zastępuje <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości, które opcje w podmenu są wyłączone, chyba że zaznaczono element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="eaf86-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="eaf86-111">Aby zaimplementować zachowanie podczas zaznaczania przycisku opcji</span><span class="sxs-lookup"><span data-stu-id="eaf86-111">To implement option-button selection behavior</span></span>  
  
1. <span data-ttu-id="eaf86-112">Inicjowanie <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość `true` umożliwiające wybór elementu.</span><span class="sxs-lookup"><span data-stu-id="eaf86-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2. <span data-ttu-id="eaf86-113">Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metodę, aby wyczyścić zaznaczenie poprzednio wybranego elementu, gdy nowy element jest wybrany.</span><span class="sxs-lookup"><span data-stu-id="eaf86-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3. <span data-ttu-id="eaf86-114">Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metodę, aby upewnić się, że kliknięcie pozycji elementu, który został już wybrany nie spowoduje wyczyszczenie zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="eaf86-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="eaf86-115">Aby zmienić wygląd elementów przycisku opcji</span><span class="sxs-lookup"><span data-stu-id="eaf86-115">To modify the appearance of the option-button items</span></span>  
  
1. <span data-ttu-id="eaf86-116">Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metodę, aby zastąpić za pomocą przycisku opcji znacznik wyboru domyślnego <xref:System.Windows.Forms.RadioButtonRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="eaf86-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2. <span data-ttu-id="eaf86-117">Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, i <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> metod w celu śledzenia stanu myszy oraz upewnij się, że <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metoda maluje stan prawidłowy przycisku opcji.</span><span class="sxs-lookup"><span data-stu-id="eaf86-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="eaf86-118">Aby wyłączyć opcje w podmenu, gdy element nadrzędny nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="eaf86-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1. <span data-ttu-id="eaf86-119">Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwość tak, aby element jest wyłączony, gdy ma ona nadrzędnego elementu zarówno <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> wartość `true` i <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="eaf86-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2. <span data-ttu-id="eaf86-120">Zastąp <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metodę, aby subskrybować <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zdarzenia nadrzędnego elementu.</span><span class="sxs-lookup"><span data-stu-id="eaf86-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3. <span data-ttu-id="eaf86-121">W obsłudze dla elementu nadrzędnego <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zdarzenia Unieważnij element, aby zaktualizować wyświetlane dane z nowy stan włączony.</span><span class="sxs-lookup"><span data-stu-id="eaf86-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="eaf86-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="eaf86-122">Example</span></span>  
 <span data-ttu-id="eaf86-123">W poniższym przykładzie kodu przedstawiono pełną `ToolStripRadioButtonMenuItem` klasy, a <xref:System.Windows.Forms.Form> klasy i `Program` klasę wykazać zachowanie przycisku opcji.</span><span class="sxs-lookup"><span data-stu-id="eaf86-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eaf86-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="eaf86-124">Compiling the Code</span></span>  
 <span data-ttu-id="eaf86-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="eaf86-125">This example requires:</span></span>  
  
-   <span data-ttu-id="eaf86-126">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="eaf86-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf86-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eaf86-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="eaf86-128">MenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="eaf86-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="eaf86-129">Instrukcje: implementowanie niestandardowego elementu ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="eaf86-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)

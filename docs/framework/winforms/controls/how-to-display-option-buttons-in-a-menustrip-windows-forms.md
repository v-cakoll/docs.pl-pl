---
title: "Porady: wyświetlanie przycisków opcji w formancie MenuStrip (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15f2d1492148a4b00a4b96844f546a4dc968eef6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="6d1f6-102">Porady: wyświetlanie przycisków opcji w formancie MenuStrip (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="6d1f6-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>
<span data-ttu-id="6d1f6-103">Przyciski opcji, znanej także jako przyciski radiowe, są podobne do pola wyboru z wyjątkiem tego, czy użytkownicy mogą wybrać tylko jeden z nich.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="6d1f6-104">Mimo że domyślnie <xref:System.Windows.Forms.ToolStripMenuItem> klasa nie zapewnia zachowanie przycisk opcji, klasa zapewnia zachowanie pola wyboru, które można dostosować, aby zaimplementować zachowanie przycisk opcji dla elementów menu w <xref:System.Windows.Forms.MenuStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="6d1f6-105">Gdy <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwość elementu menu jest `true`, użytkownicy mogą kliknąć element, aby przełączyć wyświetlanie znacznik wyboru.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="6d1f6-106"><xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> Właściwość wskazuje bieżący stan elementu.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="6d1f6-107">Aby zaimplementować podstawowe opcję zachowania, należy upewnić się, gdy element jest zaznaczony, ustawienie <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> właściwość poprzednio wybranego elementu do `false`.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>  
  
 <span data-ttu-id="6d1f6-108">W poniższych procedurach opisano, jak i dodatkowe funkcje w klasie, która dziedziczy <xref:System.Windows.Forms.ToolStripMenuItem> klasy.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="6d1f6-109">`ToolStripRadioButtonMenuItem` Klasa zastępuje elementy członkowskie <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> i <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> zaznaczenia działanie i wygląd przycisków opcji.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="6d1f6-110">Ponadto ta klasa zastępuje <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości, które opcje w podmenu są wyłączone, chyba że zaznaczono element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>  
  
### <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="6d1f6-111">Aby zaimplementować przycisk opcji Zaznaczenie zachowanie</span><span class="sxs-lookup"><span data-stu-id="6d1f6-111">To implement option-button selection behavior</span></span>  
  
1.  <span data-ttu-id="6d1f6-112">Inicjowanie <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> właściwości `true` umożliwia wybór elementu.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <span data-ttu-id="6d1f6-113">Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> metody, aby wyczyścić zaznaczenie poprzednio zaznaczony element w przypadku wybrania nowego elementu.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <span data-ttu-id="6d1f6-114">Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> metody, aby upewnić się, klikając elementu, który został już wybrany nie spowoduje wyczyszczenie zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="6d1f6-115">Aby zmodyfikować wygląd elementów przycisk opcji</span><span class="sxs-lookup"><span data-stu-id="6d1f6-115">To modify the appearance of the option-button items</span></span>  
  
1.  <span data-ttu-id="6d1f6-116">Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metodę, aby zastąpić znacznik wyboru domyślny przycisk opcji przy użyciu <xref:System.Windows.Forms.RadioButtonRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <span data-ttu-id="6d1f6-117">Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, i <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> metody do śledzenia stanu myszy i upewnij się, że <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> metody rysują stanu poprawne przycisk opcji.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="6d1f6-118">Wyłączenie opcji w podmenu, gdy element nadrzędny nie jest zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-118">To disable options on a submenu when the parent item is not selected</span></span>  
  
1.  <span data-ttu-id="6d1f6-119">Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> właściwości, aby element jest wyłączony, gdy ma element nadrzędny zarówno <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> wartość `true` i <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <span data-ttu-id="6d1f6-120">Zastąpienie <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> metody do subskrybowania <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zdarzenia nadrzędnego elementu.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  <span data-ttu-id="6d1f6-121">W obsłudze dla elementu nadrzędnego <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> zdarzenia unieważnienie element, aby zaktualizować wyświetlane dane z nowy stan włączony.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## <a name="example"></a><span data-ttu-id="6d1f6-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d1f6-122">Example</span></span>  
 <span data-ttu-id="6d1f6-123">W poniższym przykładzie kodu przedstawiono pełną `ToolStripRadioButtonMenuItem` klasy, a <xref:System.Windows.Forms.Form> klasy i `Program` klasy, aby zademonstrować zachowanie przycisk opcji.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d1f6-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6d1f6-124">Compiling the Code</span></span>  
 <span data-ttu-id="6d1f6-125">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6d1f6-125">This example requires:</span></span>  
  
-   <span data-ttu-id="6d1f6-126">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6d1f6-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1f6-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d1f6-127">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RadioButtonRenderer>  
 [<span data-ttu-id="6d1f6-128">MenuStrip — formant</span><span class="sxs-lookup"><span data-stu-id="6d1f6-128">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [<span data-ttu-id="6d1f6-129">Porady: Implementowanie niestandardowego elementu ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="6d1f6-129">How to: Implement a Custom ToolStripRenderer</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)

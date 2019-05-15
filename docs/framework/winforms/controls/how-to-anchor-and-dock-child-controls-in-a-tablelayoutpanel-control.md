---
title: 'Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: 7adbf9a98b25b237ee49d2689154e903d8fc0b5a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586176"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="7a265-102">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7a265-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="7a265-103"><xref:System.Windows.Forms.TableLayoutPanel> Kontrolować obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości w jego formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7a265-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="7a265-104">Aby wyrównać kontrolki podrzędnej w komórce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7a265-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="7a265-105">Utwórz <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7a265-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="7a265-106">Ustaw wartość <xref:System.Windows.Forms.TableLayoutPanel> kontrolki <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> i <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> właściwości **1**.</span><span class="sxs-lookup"><span data-stu-id="7a265-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3. <span data-ttu-id="7a265-107">Tworzenie <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7a265-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="7a265-108"><xref:System.Windows.Forms.Button> Zajmuje lewego górnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4. <span data-ttu-id="7a265-109">Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Left`.</span><span class="sxs-lookup"><span data-stu-id="7a265-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="7a265-110"><xref:System.Windows.Forms.Button> Kontrola przechodzi do przy lewej krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a265-111">To zachowanie różni się od zachowania inne kontrolki kontenera.</span><span class="sxs-lookup"><span data-stu-id="7a265-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="7a265-112">W innych formantów kontenera kontrolki podrzędnej nie powoduje przeniesienia kiedy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona i odległość między zakotwiczonej sterowania granicy kontenera nadrzędnego jest ustalony na czas <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="7a265-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5. <span data-ttu-id="7a265-113">Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="7a265-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="7a265-114"><xref:System.Windows.Forms.Button> Kontrola przechodzi do zajmować w lewym górnym rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6. <span data-ttu-id="7a265-115">Powtórz krok 5 z wartością `Top, Right` przenieść <xref:System.Windows.Forms.Button> kontrolki w prawym górnym rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="7a265-116">Powtórz tę procedurę za pomocą wartości `Bottom, Left` i `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="7a265-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="7a265-117">Do usługi stretch kontrolki podrzędnej w komórce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7a265-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="7a265-118">Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="7a265-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="7a265-119"><xref:System.Windows.Forms.Button> Zmieni się rozmiar kontrolki można rozciągnąć na komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a265-120">To zachowanie różni się od zachowania inne kontrolki kontenera.</span><span class="sxs-lookup"><span data-stu-id="7a265-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="7a265-121">W innych formantów kontenera kontrolki podrzędnej nie jest ze zmienionym rozmiarem, kiedy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona na `Left, Right` lub `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="7a265-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2. <span data-ttu-id="7a265-122">Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="7a265-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="7a265-123"><xref:System.Windows.Forms.Button> Zmieni się rozmiar kontrolki do rozciągania od górnej do dolnej krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3. <span data-ttu-id="7a265-124">Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="7a265-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="7a265-125"><xref:System.Windows.Forms.Button> Zmieni się rozmiar kontrolki do wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4. <span data-ttu-id="7a265-126">Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `None`.</span><span class="sxs-lookup"><span data-stu-id="7a265-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="7a265-127"><xref:System.Windows.Forms.Button> Zmianie rozmiaru czy wyśrodkowany w komórce formantu.</span><span class="sxs-lookup"><span data-stu-id="7a265-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5. <span data-ttu-id="7a265-128">Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="7a265-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="7a265-129"><xref:System.Windows.Forms.Button> Kontrola przechodzi do przy lewej krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="7a265-130"><xref:System.Windows.Forms.Button> Kontrolka zachowuje jego szerokość, ale jego wysokości rozmiaru do wypełnienia komórki w pionie.</span><span class="sxs-lookup"><span data-stu-id="7a265-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a265-131">To jest takie samo zachowanie, jak odbywa się w innych kontrolek w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="7a265-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6. <span data-ttu-id="7a265-132">Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="7a265-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="7a265-133"><xref:System.Windows.Forms.Button> Zmieni się rozmiar kontrolki do wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="7a265-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a265-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a265-134">Example</span></span>  
 <span data-ttu-id="7a265-135">Na poniższej ilustracji przedstawiono pięciu przycisków zakotwiczone w pięć oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórek.</span><span class="sxs-lookup"><span data-stu-id="7a265-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="7a265-136">![Zakotwiczanie formantu TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="7a265-136">![TableLayoutPanel Anchoring](./media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="7a265-137">Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone w rogach cztery oddzielne <xref:System.Windows.Forms.TableLayoutPanel> komórek.</span><span class="sxs-lookup"><span data-stu-id="7a265-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="7a265-138">![Zakotwiczanie formantu TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="7a265-138">![TableLayoutPanel Anchoring](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="7a265-139">Na poniższej ilustracji przedstawiono trzy przyciski rozciągnięte przez Zakotwiczanie w trzech oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórek.</span><span class="sxs-lookup"><span data-stu-id="7a265-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="7a265-140">![Zakotwiczanie formantu TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="7a265-140">![TableLayoutPanel Anchoring](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="7a265-141">Poniższy przykład kodu pokazuje wszystkie kombinacje <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="7a265-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7a265-142">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7a265-142">Compiling the Code</span></span>  
 <span data-ttu-id="7a265-143">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7a265-143">This example requires:</span></span>  
  
- <span data-ttu-id="7a265-144">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7a265-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a265-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a265-145">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="7a265-146">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7a265-146">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)

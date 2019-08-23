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
ms.openlocfilehash: 0e565b56c31d0776f6e89bbbe0b0681ae184758e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922821"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="8e777-102">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8e777-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="8e777-103">Kontrolka obsługuje właściwości <xref:System.Windows.Forms.Control.Dock%2A> i w jego kontrolkach podrzędnych. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="8e777-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="8e777-104">Aby wyrównać formant podrzędny w komórce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8e777-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="8e777-105"><xref:System.Windows.Forms.TableLayoutPanel> Utwórz kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="8e777-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="8e777-106">Ustaw wartość <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> kontrolki i właściwości na **1.** <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A></span><span class="sxs-lookup"><span data-stu-id="8e777-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3. <span data-ttu-id="8e777-107">Utwórz kontrolkę w <xref:System.Windows.Forms.TableLayoutPanel>kontrolce. <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="8e777-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="8e777-108">W <xref:System.Windows.Forms.Button> lewym górnym rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="8e777-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4. <span data-ttu-id="8e777-109">Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Left`.</span><span class="sxs-lookup"><span data-stu-id="8e777-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="8e777-110"><xref:System.Windows.Forms.Button> Kontrolka przenosi się do obszaru Wyrównaj do lewej krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="8e777-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e777-111">To zachowanie różni się od zachowania innych kontrolek kontenera.</span><span class="sxs-lookup"><span data-stu-id="8e777-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="8e777-112">W innych kontrolkach kontenera formant podrzędny nie jest przenoszony, gdy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona, a odległość między kontrolką zakotwiczoną a granicą kontenera nadrzędnego jest ustalana w <xref:System.Windows.Forms.Control.Anchor%2A> momencie ustawienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="8e777-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5. <span data-ttu-id="8e777-113">Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="8e777-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="8e777-114"><xref:System.Windows.Forms.Button> Formant przesuwa się w celu założenia lewego górnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="8e777-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6. <span data-ttu-id="8e777-115">Powtórz krok 5 z wartością `Top, Right` , aby <xref:System.Windows.Forms.Button> przenieść formant do prawego górnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="8e777-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="8e777-116">Powtarzaj wartości `Bottom, Left` i `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="8e777-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="8e777-117">Aby rozciągnąć formant podrzędny w komórce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8e777-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1. <span data-ttu-id="8e777-118">Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="8e777-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="8e777-119">Rozmiar <xref:System.Windows.Forms.Button> formantu zostanie zmieniony w celu rozciągnięcia w całej komórce.</span><span class="sxs-lookup"><span data-stu-id="8e777-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e777-120">To zachowanie różni się od zachowania innych kontrolek kontenera.</span><span class="sxs-lookup"><span data-stu-id="8e777-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="8e777-121">W innych kontrolkach kontenera nie zmienia się rozmiar kontrolki podrzędnej, gdy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona na `Left, Right` lub `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="8e777-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2. <span data-ttu-id="8e777-122">Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="8e777-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="8e777-123">Rozmiar <xref:System.Windows.Forms.Button> formantu zostanie zmieniony w celu rozciągnięcia od góry do dołu komórki.</span><span class="sxs-lookup"><span data-stu-id="8e777-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3. <span data-ttu-id="8e777-124">Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="8e777-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="8e777-125">Rozmiar <xref:System.Windows.Forms.Button> kontrolki zostanie zmieniony w celu wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="8e777-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4. <span data-ttu-id="8e777-126">Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `None`.</span><span class="sxs-lookup"><span data-stu-id="8e777-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="8e777-127">Rozmiar <xref:System.Windows.Forms.Button> formantu został zmieniony i wyśrodkowany w komórce.</span><span class="sxs-lookup"><span data-stu-id="8e777-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5. <span data-ttu-id="8e777-128">Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Dock%2A> właściwości kontrolki na <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="8e777-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="8e777-129"><xref:System.Windows.Forms.Button> Kontrolka przenosi się do obszaru Wyrównaj do lewej krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="8e777-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="8e777-130"><xref:System.Windows.Forms.Button> Kontrolka zachowuje swoją szerokość, ale jej wysokość jest zmieniana, aby wypełnić komórkę w pionie.</span><span class="sxs-lookup"><span data-stu-id="8e777-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8e777-131">Jest to takie samo zachowanie, jak w przypadku innych kontrolek kontenera.</span><span class="sxs-lookup"><span data-stu-id="8e777-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6. <span data-ttu-id="8e777-132">Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Dock%2A> właściwości kontrolki na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="8e777-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="8e777-133">Rozmiar <xref:System.Windows.Forms.Button> kontrolki zostanie zmieniony w celu wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="8e777-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e777-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e777-134">Example</span></span>  
 <span data-ttu-id="8e777-135">Na poniższej ilustracji przedstawiono pięć przycisków zakotwiczonych w pięciu oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórkach.</span><span class="sxs-lookup"><span data-stu-id="8e777-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="8e777-136">![Zakotwiczanie TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="8e777-136">![TableLayoutPanel Anchoring](./media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="8e777-137">Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone w rogach czterech oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórek.</span><span class="sxs-lookup"><span data-stu-id="8e777-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="8e777-138">![Zakotwiczanie TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="8e777-138">![TableLayoutPanel Anchoring](./media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="8e777-139">Poniższa ilustracja przedstawia trzy przyciski rozciągane przez zakotwiczenie w trzech oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórkach.</span><span class="sxs-lookup"><span data-stu-id="8e777-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="8e777-140">![Zakotwiczanie TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="8e777-140">![TableLayoutPanel Anchoring](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="8e777-141">Poniższy przykład kodu demonstruje wszystkie kombinacje <xref:System.Windows.Forms.Control.Anchor%2A> wartości <xref:System.Windows.Forms.Button> właściwości kontrolki <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="8e777-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e777-142">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8e777-142">Compiling the Code</span></span>  
 <span data-ttu-id="8e777-143">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="8e777-143">This example requires:</span></span>  
  
- <span data-ttu-id="8e777-144">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="8e777-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e777-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e777-145">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="8e777-146">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8e777-146">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)

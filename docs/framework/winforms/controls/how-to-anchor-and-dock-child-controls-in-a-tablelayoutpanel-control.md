---
title: "Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56909c823beca99d277bfbf7a20d39663bcd44ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="5cb8c-102">Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5cb8c-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="5cb8c-103"><xref:System.Windows.Forms.TableLayoutPanel> Sterowanie obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości w jej kontrolkach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="5cb8c-104">Aby wyrównać kontrolki podrzędnej w komórce formantu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5cb8c-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="5cb8c-105">Utwórz <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="5cb8c-106">Ustaw wartość <xref:System.Windows.Forms.TableLayoutPanel> formantu <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> i <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> właściwości **1**.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3.  <span data-ttu-id="5cb8c-107">Utwórz <xref:System.Windows.Forms.Button> kontroli w <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="5cb8c-108"><xref:System.Windows.Forms.Button> Zajmuje lewego górnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4.  <span data-ttu-id="5cb8c-109">Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Left`.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="5cb8c-110"><xref:System.Windows.Forms.Button> Kontroli przenosi do zapewnienia zgodności z lewej krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5cb8c-111">To zachowanie różni się od zachowania inne formanty kontenera.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="5cb8c-112">W innych kontrolek kontenera formant podrzędny nie przenosi kiedy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona, a odległość między zakotwiczonej kontroli i granic kontenera nadrzędnego jest ustalone w czasie <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5.  <span data-ttu-id="5cb8c-113">Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="5cb8c-114"><xref:System.Windows.Forms.Button> Kontroli przenosi zajmować lewego górnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6.  <span data-ttu-id="5cb8c-115">Powtórz krok 5 z wartością `Top, Right` można przenieść <xref:System.Windows.Forms.Button> formantu prawym górnym rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="5cb8c-116">Powtarzania z wartościami `Bottom, Left` i `Bottom, Right`.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="5cb8c-117">Aby rozciągnąć formant podrzędny w komórce formantu TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5cb8c-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="5cb8c-118">Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="5cb8c-119"><xref:System.Windows.Forms.Button> Do rozciągania między komórki zostanie zmieniony rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5cb8c-120">To zachowanie różni się od zachowania inne formanty kontenera.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="5cb8c-121">W innych kontrolek kontenera formant podrzędny nie jest zmiany rozmiaru, kiedy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona na `Left, Right` lub `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2.  <span data-ttu-id="5cb8c-122">Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Top, Bottom`.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="5cb8c-123"><xref:System.Windows.Forms.Button> Do rozciągania od góry do dołu komórki zostanie zmieniony rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3.  <span data-ttu-id="5cb8c-124">Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Top, Bottom, Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="5cb8c-125"><xref:System.Windows.Forms.Button> Do wypełnienia komórki zostanie zmieniony rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4.  <span data-ttu-id="5cb8c-126">Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `None`.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="5cb8c-127"><xref:System.Windows.Forms.Button> Zmiany rozmiaru i wyśrodkowany w komórce kontroli.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5.  <span data-ttu-id="5cb8c-128">Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Left>.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="5cb8c-129"><xref:System.Windows.Forms.Button> Kontroli przenosi do zapewnienia zgodności z lewej krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="5cb8c-130"><xref:System.Windows.Forms.Button> Formant zachowuje szerokości, ale jego wysokości rozmiaru do wypełnienia komórki w pionie.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5cb8c-131">To samo występujący w innych kontrolek w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6.  <span data-ttu-id="5cb8c-132">Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="5cb8c-133"><xref:System.Windows.Forms.Button> Do wypełnienia komórki zostanie zmieniony rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cb8c-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cb8c-134">Example</span></span>  
 <span data-ttu-id="5cb8c-135">Na poniższej ilustracji przedstawiono pięciu przycisków zakotwiczonych w oddzielnych pięć <xref:System.Windows.Forms.TableLayoutPanel> komórek.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="5cb8c-136">![Zakotwiczanie formantu TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="5cb8c-136">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="5cb8c-137">Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczonych w narożnikach cztery oddzielne <xref:System.Windows.Forms.TableLayoutPanel> komórek.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="5cb8c-138">![Zakotwiczanie formantu TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="5cb8c-138">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="5cb8c-139">Na poniższej ilustracji przedstawiono trzy przyciski rozciągnięty przez Zakotwiczanie w trzech osobnych <xref:System.Windows.Forms.TableLayoutPanel> komórek.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="5cb8c-140">![Zakotwiczanie formantu TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="5cb8c-140">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="5cb8c-141">Poniższy przykład kodu pokazuje wszystkie kombinacje <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> kontroli w <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cb8c-142">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5cb8c-142">Compiling the Code</span></span>  
 <span data-ttu-id="5cb8c-143">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5cb8c-143">This example requires:</span></span>  
  
-   <span data-ttu-id="5cb8c-144">Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5cb8c-145">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5cb8c-145">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5cb8c-146">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="5cb8c-146">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="5cb8c-147">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="5cb8c-147">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cb8c-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cb8c-148">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="5cb8c-149">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5cb8c-149">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)

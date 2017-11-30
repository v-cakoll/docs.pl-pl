---
title: "Porady: aranżowanie formantów z liniami przyciągania oraz siatki w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GridSize
helpviewer_keywords:
- snap to grid [Windows Forms], Windows Forms Designer
- Windows Forms, grid options in designer
- controls [Windows Forms], aligning
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ab199f390fa6a704ad3b3d2a17387d034cf2e57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="a5a67-102">Porady: aranżowanie formantów z liniami przyciągania oraz siatki w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a5a67-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="a5a67-103">Przy użyciu funkcji układu [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], możesz dokładnie wskazać rozmieszczenie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a5a67-103">Using the layout features of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="a5a67-104">Formanty dodane do formularza lub przeniesione w formularzu zostanie automatycznie wyrównany do wierszy i kolumn siatki projektanta formularzy systemu Windows lub można wyrównywanie formantów za pomocą funkcji linie przyciągania.</span><span class="sxs-lookup"><span data-stu-id="a5a67-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5a67-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="a5a67-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a5a67-106">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="a5a67-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a5a67-107">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="a5a67-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="a5a67-108">Przyciągania wszystkie formanty do siatki</span><span class="sxs-lookup"><span data-stu-id="a5a67-108">To snap all controls to the grid</span></span>  
  
-   <span data-ttu-id="a5a67-109">Wybierz **SnapToGrid** tryb układu w narzędziu Projektant dla formularzy systemu Windows **opcje** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a5a67-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="a5a67-110">Aby uzyskać więcej informacji, zobacz [ogólne, Projektant formularzy systemu Windows, opcje — Okno dialogowe](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).</span><span class="sxs-lookup"><span data-stu-id="a5a67-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).</span></span> <span data-ttu-id="a5a67-111">Wszystkie formanty teraz przyłączenie wzdłuż punktów w siatce.</span><span class="sxs-lookup"><span data-stu-id="a5a67-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="a5a67-112">Pojedynczych formantów do siatki mogą być przyciągane blokując w miejscu.</span><span class="sxs-lookup"><span data-stu-id="a5a67-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="a5a67-113">Jednakże gdy są one zablokowane, ich nie można przenosić ani zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="a5a67-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="a5a67-114">Aby uzyskać więcej informacji na temat blokowania formantów, zobacz [porady: blokowanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a5a67-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="a5a67-115">Aby wyrównać formantów za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="a5a67-115">To align controls using snaplines</span></span>  
  
-   <span data-ttu-id="a5a67-116">Wybierz **linie przyciągania** tryb układu w narzędziu Projektant dla formularzy systemu Windows **opcje** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a5a67-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="a5a67-117">Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów na formularzach systemu Windows przy użyciu linie przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="a5a67-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="a5a67-118">Linie przyciągania umożliwia teraz wyrównywanie i rozmieszczanie formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a5a67-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a67-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5a67-119">See Also</span></span>  
 [<span data-ttu-id="a5a67-120">Ogólne, Projektant formularzy systemu Windows, opcje — Okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="a5a67-120">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="a5a67-121">Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="a5a67-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="a5a67-122">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a5a67-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="a5a67-123">Porady: dodawanie formantów do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a5a67-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="a5a67-124">Rozmieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a5a67-124">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="a5a67-125">Etykietowanie formantów formularzy systemu Windows poszczególnych i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="a5a67-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="a5a67-126">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a5a67-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="a5a67-127">Formanty przez funkcję formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a5a67-127">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)

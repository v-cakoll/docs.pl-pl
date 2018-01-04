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
ms.workload: dotnet
ms.openlocfilehash: 7e3754df2930503e7e7a123ffdb4d4b787338c20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="907b4-102">Porady: aranżowanie formantów z liniami przyciągania oraz siatki w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="907b4-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="907b4-103">Przy użyciu funkcji układu [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], możesz dokładnie wskazać rozmieszczenie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="907b4-103">Using the layout features of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="907b4-104">Formanty dodane do formularza lub przeniesione w formularzu zostanie automatycznie wyrównany do wierszy i kolumn siatki projektanta formularzy systemu Windows lub można wyrównywanie formantów za pomocą funkcji linie przyciągania.</span><span class="sxs-lookup"><span data-stu-id="907b4-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="907b4-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="907b4-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="907b4-106">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="907b4-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="907b4-107">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="907b4-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="907b4-108">Przyciągania wszystkie formanty do siatki</span><span class="sxs-lookup"><span data-stu-id="907b4-108">To snap all controls to the grid</span></span>  
  
-   <span data-ttu-id="907b4-109">Wybierz **SnapToGrid** tryb układu w narzędziu Projektant dla formularzy systemu Windows **opcje** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="907b4-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="907b4-110">Aby uzyskać więcej informacji, zobacz [ogólne, Projektant formularzy systemu Windows, opcje — Okno dialogowe](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).</span><span class="sxs-lookup"><span data-stu-id="907b4-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).</span></span> <span data-ttu-id="907b4-111">Wszystkie formanty teraz przyłączenie wzdłuż punktów w siatce.</span><span class="sxs-lookup"><span data-stu-id="907b4-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="907b4-112">Pojedynczych formantów do siatki mogą być przyciągane blokując w miejscu.</span><span class="sxs-lookup"><span data-stu-id="907b4-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="907b4-113">Jednakże gdy są one zablokowane, ich nie można przenosić ani zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="907b4-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="907b4-114">Aby uzyskać więcej informacji na temat blokowania formantów, zobacz [porady: blokowanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="907b4-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="907b4-115">Aby wyrównać formantów za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="907b4-115">To align controls using snaplines</span></span>  
  
-   <span data-ttu-id="907b4-116">Wybierz **linie przyciągania** tryb układu w narzędziu Projektant dla formularzy systemu Windows **opcje** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="907b4-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="907b4-117">Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów na formularzach systemu Windows przy użyciu linie przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="907b4-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="907b4-118">Linie przyciągania umożliwia teraz wyrównywanie i rozmieszczanie formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="907b4-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="907b4-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="907b4-119">See Also</span></span>  
 [<span data-ttu-id="907b4-120">Ogólne, Projektant formularzy systemu Windows, opcje — Okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="907b4-120">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="907b4-121">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="907b4-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="907b4-122">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907b4-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="907b4-123">Instrukcje: dodawanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907b4-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="907b4-124">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907b4-124">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="907b4-125">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="907b4-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="907b4-126">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907b4-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="907b4-127">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="907b4-127">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)

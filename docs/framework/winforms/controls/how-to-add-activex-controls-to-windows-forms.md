---
title: 'Porady: dodawanie kontrolek ActiveX do formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: afee07f2f5009abb6cf8facc94b138f4ea2a11fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="2ad64-102">Porady: dodawanie kontrolek ActiveX do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ad64-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="2ad64-103">Gdy Projektant formularzy systemu Windows jest zoptymalizowany do hosta formanty formularzy systemu Windows, można również wprowadzić formantów na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2ad64-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2ad64-104">Istnieją ograniczenia dotyczące wydajności dla formularzy systemu Windows, po dodaniu formantów ActiveX do nich.</span><span class="sxs-lookup"><span data-stu-id="2ad64-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="2ad64-105">Przed dodaniem formantów ActiveX na formularzu, należy dodać je do przybornika.</span><span class="sxs-lookup"><span data-stu-id="2ad64-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="2ad64-106">Aby uzyskać więcej informacji, zobacz [składników modelu COM, dostosowywanie przybornika — okno dialogowe](http://msdn.microsoft.com/en-us/171333f3-f207-4e02-bbdc-17862556212c).</span><span class="sxs-lookup"><span data-stu-id="2ad64-106">For more information, see [COM Components, Customize Toolbox Dialog Box](http://msdn.microsoft.com/en-us/171333f3-f207-4e02-bbdc-17862556212c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ad64-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="2ad64-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2ad64-108">Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="2ad64-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2ad64-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="2ad64-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="2ad64-110">Aby dodać kontrolki ActiveX na formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ad64-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="2ad64-111">Kliknij dwukrotnie formant w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="2ad64-111">Double-click the control on the Toolbox.</span></span>  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]<span data-ttu-id="2ad64-112">dodaje wszystkie odwołania do formantu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2ad64-112"> adds all references to the control in your project.</span></span> <span data-ttu-id="2ad64-113">Aby uzyskać więcej informacji dotyczących kwestii, które należy wziąć pod uwagę, gdy za pomocą formantów na formularzach systemu Windows, zobacz [uwagi odnośnie do hostowania kontrolki ActiveX na formularzu systemu Windows](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="2ad64-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ad64-114">Importer kontrolki ActiveX formularzy systemu Windows (AxImp.exe) tworzy argumenty zdarzeń innego typu niż oczekiwano na Import biblioteki dołączanej dynamicznie ActiveX.</span><span class="sxs-lookup"><span data-stu-id="2ad64-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="2ad64-115">Argumenty utworzone przez AxImp.exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` jest oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="2ad64-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="2ad64-116">Należy pamiętać, że ta nieprawidłowości nie zapobiega kod działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="2ad64-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="2ad64-117">Aby uzyskać więcej informacji, zobacz [Importer kontrolki ActiveX formularzy systemu Windows (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="2ad64-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad64-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ad64-118">See Also</span></span>  
 [<span data-ttu-id="2ad64-119">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ad64-119">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="2ad64-120">Formanty i obiektów programowalnych w różnych językach i biblioteki</span><span class="sxs-lookup"><span data-stu-id="2ad64-120">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/en-us/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="2ad64-121">Porady: dodawanie formantów do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ad64-121">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="2ad64-122">Rozmieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ad64-122">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="2ad64-123">Etykietowanie formantów formularzy systemu Windows poszczególnych i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="2ad64-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="2ad64-124">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ad64-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="2ad64-125">Formanty przez funkcję formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ad64-125">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)

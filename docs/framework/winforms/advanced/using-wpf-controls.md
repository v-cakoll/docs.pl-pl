---
title: "Korzystanie z formantów WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c14da85b377b3ef80d6accbc8b0319959a75bcd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-wpf-controls"></a><span data-ttu-id="d694b-102">Korzystanie z formantów WPF</span><span class="sxs-lookup"><span data-stu-id="d694b-102">Using WPF Controls</span></span>
<span data-ttu-id="d694b-103">Formanty Windows Presentation Foundation (WPF) służy w aplikacjach opartych na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d694b-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="d694b-104">Chociaż te dwie technologie inny widok, ich współdziałać sprawnie.</span><span class="sxs-lookup"><span data-stu-id="d694b-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="d694b-105">Projektant formularzy systemu Windows udostępnia środowisko wizualnego projektu do hostowania kontrolki Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="d694b-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="d694b-106">Formant WPF jest hostowana przez specjalne formantu formularzy systemu Windows o nazwie <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="d694b-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="d694b-107">Ten formant umożliwia kontrolce WPF do udziału w układu formularza i odbierać komunikaty klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="d694b-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="d694b-108">W czasie projektowania, można rozmieścić <xref:System.Windows.Forms.Integration.ElementHost> sterować tak samo jak dowolnej kontrolki formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d694b-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="d694b-109">Formanty formularzy systemu Windows umożliwia także w aplikacjach opartych na WPF.</span><span class="sxs-lookup"><span data-stu-id="d694b-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="d694b-110">Aby uzyskać więcej informacji, zobacz [projektanta WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26).</span><span class="sxs-lookup"><span data-stu-id="d694b-110">For more information, see [WPF Designer](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d694b-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d694b-111">In This Section</span></span>  
 [<span data-ttu-id="d694b-112">Instrukcje: kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d694b-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="d694b-113">Przedstawia sposób kopiowania formantu Windows Presentation Foundation na formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d694b-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="d694b-114">Przewodnik: rozmieszczanie zawartości WPF na formularzach Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d694b-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="d694b-115">Przedstawia sposób korzystania z funkcji układ formularzy systemu Windows, takich jak Zakotwiczanie i linie przyciągania, ułożyć kontrolki Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="d694b-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>  
  
 [<span data-ttu-id="d694b-116">Przewodnik: zmienianie właściwości hostowanego elementu WPF w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d694b-116">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 <span data-ttu-id="d694b-117">Przedstawiono przepływ pracy między Projektant formularzy systemu Windows i [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] zmiany właściwości formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="d694b-117">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] for changing properties on WPF controls.</span></span>  
  
 [<span data-ttu-id="d694b-118">Przewodnik: tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d694b-118">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="d694b-119">Przedstawia sposób tworzenia kontrolki Windows Presentation Foundation, do użycia w aplikacjach opartych na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d694b-119">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>  
  
 [<span data-ttu-id="d694b-120">Przewodnik: kopiowanie i wklejanie kontrolki ElementHost w oddzielnych formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d694b-120">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 <span data-ttu-id="d694b-121">Przedstawia sposób kopiowania kontrolki Windows Presentation Foundation z jednego formularza systemu Windows na inny.</span><span class="sxs-lookup"><span data-stu-id="d694b-121">Shows how to copy a Windows Presentation Foundation control from one Windows Form to another.</span></span>  
  
 [<span data-ttu-id="d694b-122">Przewodnik: przypisywanie zawartości WPF na formularzach Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d694b-122">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="d694b-123">Pokazuje, jak wybrać typy formantów systemu Windows Presentation Foundation, które mają być wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="d694b-123">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="d694b-124">Przewodnik: nadawanie stylu zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="d694b-124">Walkthrough: Styling WPF Content</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="d694b-125">Przedstawiono przepływ pracy między Projektant formularzy systemu Windows i [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] stosowania stylów do kontrolki Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="d694b-125">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d694b-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d694b-126">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="d694b-127">W tym artykule opisano klasy, która służy do kontrolki Windows Presentation Foundation hosta w aplikacjach opartych na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d694b-127">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="d694b-128">W tym artykule opisano klasy, która służy do hosta formanty formularzy systemu Windows w aplikacji opartej na systemie Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="d694b-128">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d694b-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d694b-129">Related Sections</span></span>  
 [<span data-ttu-id="d694b-130">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d694b-130">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="d694b-131">Opisuje współdziałanie między technologii Windows Presentation Foundation i formularze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d694b-131">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="d694b-132">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="d694b-132">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 <span data-ttu-id="d694b-133">Opisuje sposób projektowania kontrolek Windows Presentation Foundation w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d694b-133">Describes how to design Windows Presentation Foundation controls in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>

---
title: Korzystanie z formantów WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: be925bdceea3dd01c568d85fe025d6e037066454
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48778211"
---
# <a name="using-wpf-controls"></a><span data-ttu-id="e70b4-102">Korzystanie z formantów WPF</span><span class="sxs-lookup"><span data-stu-id="e70b4-102">Using WPF Controls</span></span>
<span data-ttu-id="e70b4-103">W aplikacjach opartych na formularzach Windows, można użyć kontrolek Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="e70b4-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="e70b4-104">Mimo że są to dwie technologie inny widok, mogą współdziałać sprawnie.</span><span class="sxs-lookup"><span data-stu-id="e70b4-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="e70b4-105">Windows Forms Designer udostępnia środowisko projektowania wizualnego do hostowania kontrolki Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="e70b4-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="e70b4-106">Kontrolki WPF jest hostowana przez kontrolkę Windows Forms specjalne, o nazwie <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="e70b4-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="e70b4-107">Ten formant umożliwia formantu WPF do wzięcia udziału w układzie formularza i odbierać komunikaty klawiatury i myszy.</span><span class="sxs-lookup"><span data-stu-id="e70b4-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="e70b4-108">W czasie projektowania, można rozmieścić <xref:System.Windows.Forms.Integration.ElementHost> sterować tak samo jak dowolnej kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e70b4-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="e70b4-109">Umożliwia także kontrolek formularzy Windows Forms w swoich aplikacjach opartego na podsystemie WPF.</span><span class="sxs-lookup"><span data-stu-id="e70b4-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="e70b4-110">Aby uzyskać więcej informacji, zobacz [projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="e70b4-110">For more information, see [Design XAML in Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e70b4-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e70b4-111">In This Section</span></span>  
 [<span data-ttu-id="e70b4-112">Instrukcje: kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="e70b4-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="e70b4-113">Pokazuje, jak kopiowanie kontrolki Windows Presentation Foundation w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="e70b4-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="e70b4-114">Przewodnik: rozmieszczanie zawartości WPF na formularzach Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="e70b4-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="e70b4-115">Pokazuje, jak korzystać z funkcji układu formularzy Windows, takich jak Zakotwiczanie i linii przyciągania, aby rozmieścić formanty Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="e70b4-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>
  
 [<span data-ttu-id="e70b4-116">Przewodnik: tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="e70b4-116">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="e70b4-117">Pokazuje, jak utworzyć formant programu Windows Presentation Foundation, do użytku w aplikacjach opartych na formularzach Windows.</span><span class="sxs-lookup"><span data-stu-id="e70b4-117">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>
  
 [<span data-ttu-id="e70b4-118">Przewodnik: przypisywanie zawartości WPF na formularzach Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="e70b4-118">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="e70b4-119">Pokazuje sposób wybierania typów formantów Windows Presentation Foundation, które mają być wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e70b4-119">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="e70b4-120">Przewodnik: nadawanie stylu zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="e70b4-120">Walkthrough: Styling WPF Content</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="e70b4-121">Przedstawia przepływ pracy między Windows Forms Designer i [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] dla stosowanie stylów do kontrolek Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="e70b4-121">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e70b4-122">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e70b4-122">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="e70b4-123">W tym artykule opisano klasy, które służy do kontrolek Windows Presentation Foundation hosta w swoich aplikacjach opartych na formularzach Windows.</span><span class="sxs-lookup"><span data-stu-id="e70b4-123">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="e70b4-124">W tym artykule opisano klasy, które służy do kontrolek Windows Forms hosta w aplikacji opartej na systemie Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="e70b4-124">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e70b4-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e70b4-125">Related Sections</span></span>  
 [<span data-ttu-id="e70b4-126">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="e70b4-126">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="e70b4-127">W tym artykule opisano współdziałanie technologii Windows Presentation Foundation i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e70b4-127">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="e70b4-128">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e70b4-128">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)  
 <span data-ttu-id="e70b4-129">Opisuje sposób projektowania formanty Windows Presentation Foundation w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e70b4-129">Describes how to design Windows Presentation Foundation controls in Visual Studio.</span></span>

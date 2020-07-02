---
title: Tworzenie niestandardowych kontrolek
description: Dowiedz się więcej o kontrolkach formularzy systemu Windows. W tym celu dowiesz się, jak połączyć istniejące kontrolki, zwiększyć istniejące kontrolki i utworzyć własne kontrolki niestandardowe.
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 12013496c9650489fdd7512206317000fc0ec78c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618379"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="f6ed7-104">Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6ed7-104">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="f6ed7-105">Formanty Windows Forms to składniki wielokrotnego użytku, które hermetyzują funkcje interfejsu użytkownika i są używane w aplikacjach systemu Windows po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-105">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="f6ed7-106">Nie tylko Windows Forms udostępniają wiele gotowych do użycia kontrolek, a także udostępniają infrastrukturę do tworzenia własnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-106">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="f6ed7-107">Możesz łączyć istniejące kontrolki, rozwijać istniejące kontrolki lub tworzyć własne niestandardowe kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-107">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="f6ed7-108">W tej sekcji znajdują się informacje i przykłady, które ułatwiają opracowywanie Windows Formsch kontrolek.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-108">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6ed7-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f6ed7-109">In This Section</span></span>  
 [<span data-ttu-id="f6ed7-110">Omówienie używania formantów w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f6ed7-110">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="f6ed7-111">Wyróżnia najważniejsze elementy z używania formantów w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-111">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="f6ed7-112">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f6ed7-112">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="f6ed7-113">Opisuje różne rodzaje niestandardowych kontrolek, które można tworzyć przy użyciu <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-113">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="f6ed7-114">Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6ed7-114">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="f6ed7-115">W tym artykule omówiono pierwsze kroki tworzenia kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-115">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="f6ed7-116">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6ed7-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="f6ed7-117">Pokazuje, jak dodać do właściwości do kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-117">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="f6ed7-118">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6ed7-118">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="f6ed7-119">Pokazuje, jak obsługiwać i definiować zdarzenia w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-119">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="f6ed7-120">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6ed7-120">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="f6ed7-121">Opisuje atrybuty, które można zastosować do właściwości lub innych elementów niestandardowych formantów i składników.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-121">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="f6ed7-122">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f6ed7-122">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="f6ed7-123">Pokazuje, jak dostosować wygląd kontrolek.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-123">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="f6ed7-124">Układ w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f6ed7-124">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="f6ed7-125">Pokazuje, jak tworzyć zaawansowane układy formantów i formularzy.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-125">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="f6ed7-126">Wielowątkowość w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f6ed7-126">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="f6ed7-127">Pokazuje sposób implementacji formantów wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-127">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f6ed7-128">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="f6ed7-128">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="f6ed7-129">Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-129">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="f6ed7-130">Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-130">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f6ed7-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f6ed7-131">Related Sections</span></span>  
 <span data-ttu-id="f6ed7-132">[Atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f6ed7-132">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="f6ed7-133">Wyświetla listę atrybutów metadanych, które mają zostać zastosowane do składników i formantów, aby były wyświetlane prawidłowo w czasie projektowania w projektantach wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-133">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="f6ed7-134">[Rozszerzona pomoc techniczna czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f6ed7-134">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="f6ed7-135">Opisuje sposób implementacji klas, takich jak redaktorzy i projektanci, które zapewniają obsługę czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-135">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="f6ed7-136">[Porady: licencjonowanie składników i kontrolek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="f6ed7-136">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="f6ed7-137">Opisuje sposób implementacji licencjonowania w kontrolce lub składniku.</span><span class="sxs-lookup"><span data-stu-id="f6ed7-137">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="f6ed7-138">Zobacz również [Opracowywanie formantów Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f6ed7-138">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>

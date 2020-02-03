---
title: Tworzenie niestandardowych kontrolek
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 9dbc1c4530b3a0f4e579ca67c7ae88c1685222ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746001"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="5729a-102">Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5729a-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="5729a-103">Formanty Windows Forms to składniki wielokrotnego użytku, które hermetyzują funkcje interfejsu użytkownika i są używane w aplikacjach systemu Windows po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="5729a-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="5729a-104">Nie tylko Windows Forms udostępniają wiele gotowych do użycia kontrolek, a także udostępniają infrastrukturę do tworzenia własnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="5729a-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="5729a-105">Możesz łączyć istniejące kontrolki, rozwijać istniejące kontrolki lub tworzyć własne niestandardowe kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5729a-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="5729a-106">W tej sekcji znajdują się informacje i przykłady, które ułatwiają opracowywanie Windows Formsch kontrolek.</span><span class="sxs-lookup"><span data-stu-id="5729a-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5729a-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5729a-107">In This Section</span></span>  
 [<span data-ttu-id="5729a-108">Omówienie używania kontrolek w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5729a-108">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="5729a-109">Wyróżnia najważniejsze elementy z używania formantów w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5729a-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="5729a-110">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="5729a-110">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="5729a-111">Opisuje różne rodzaje niestandardowych kontrolek, które można tworzyć za pomocą przestrzeni nazw <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5729a-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="5729a-112">Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5729a-112">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="5729a-113">W tym artykule omówiono pierwsze kroki tworzenia kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5729a-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="5729a-114">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5729a-114">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="5729a-115">Pokazuje, jak dodać do właściwości do kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5729a-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="5729a-116">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5729a-116">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="5729a-117">Pokazuje, jak obsługiwać i definiować zdarzenia w kontrolkach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5729a-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="5729a-118">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5729a-118">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="5729a-119">Opisuje atrybuty, które można zastosować do właściwości lub innych elementów niestandardowych formantów i składników.</span><span class="sxs-lookup"><span data-stu-id="5729a-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="5729a-120">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="5729a-120">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="5729a-121">Pokazuje, jak dostosować wygląd kontrolek.</span><span class="sxs-lookup"><span data-stu-id="5729a-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="5729a-122">Układ w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5729a-122">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="5729a-123">Pokazuje, jak tworzyć zaawansowane układy formantów i formularzy.</span><span class="sxs-lookup"><span data-stu-id="5729a-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="5729a-124">Wielowątkowość w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5729a-124">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="5729a-125">Pokazuje sposób implementacji formantów wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="5729a-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5729a-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="5729a-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="5729a-127">Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5729a-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="5729a-128">Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5729a-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5729a-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5729a-129">Related Sections</span></span>  
 <span data-ttu-id="5729a-130">[Atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="5729a-130">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="5729a-131">Wyświetla listę atrybutów metadanych, które mają zostać zastosowane do składników i formantów, aby były wyświetlane prawidłowo w czasie projektowania w projektantach wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="5729a-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="5729a-132">[Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="5729a-132">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="5729a-133">Opisuje sposób implementacji klas, takich jak redaktorzy i projektanci, które zapewniają obsługę czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="5729a-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="5729a-134">[Instrukcje: składniki i kontrolki licencji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="5729a-134">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="5729a-135">Opisuje sposób implementacji licencjonowania w kontrolce lub składniku.</span><span class="sxs-lookup"><span data-stu-id="5729a-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="5729a-136">Zobacz również [Opracowywanie formantów Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="5729a-136">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>

---
title: Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 3d628d75b75c311c266648886b3b971c4833d172
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716442"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="08d5f-102">Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="08d5f-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="08d5f-103">Kontrolek formularzy Windows Forms są składniki wielokrotnego użytku, hermetyzacji funkcjonalność interfejsu użytkownika, które są używane w aplikacjach opartych na Windows po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="08d5f-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="08d5f-104">Nie tylko formularze Windows zapewnia wiele kontrolek gotowych do użycia, również udostępnia infrastrukturę do tworzenia własnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="08d5f-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="08d5f-105">Można połączyć istniejące kontrolki, rozszerzanie istniejących kontrolek lub tworzyć własne niestandardowe formanty.</span><span class="sxs-lookup"><span data-stu-id="08d5f-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="08d5f-106">Ta sekcja zawiera ogólne informacje i przykłady ułatwiające opracowywanie kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08d5f-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08d5f-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="08d5f-107">In This Section</span></span>  
 [<span data-ttu-id="08d5f-108">Omówienie używania kontrolek w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08d5f-108">Overview of Using Controls in Windows Forms</span></span>](overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="08d5f-109">Podświetla podstawowe elementy za pomocą formantów w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08d5f-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="08d5f-110">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="08d5f-110">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)  
 <span data-ttu-id="08d5f-111">W tym artykule opisano różne rodzaje Kontrolki niestandardowe można tworzyć za pomocą <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="08d5f-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="08d5f-112">Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08d5f-112">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)  
 <span data-ttu-id="08d5f-113">W tym artykule omówiono pierwszych kroków w tworzeniu formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08d5f-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="08d5f-114">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08d5f-114">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)  
 <span data-ttu-id="08d5f-115">Pokazuje, jak dodać do właściwości kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08d5f-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="08d5f-116">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08d5f-116">Events in Windows Forms Controls</span></span>](events-in-windows-forms-controls.md)  
 <span data-ttu-id="08d5f-117">Pokazuje, jak obsługiwać i definiowania zdarzenia w kontrolkach formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="08d5f-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="08d5f-118">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08d5f-118">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="08d5f-119">W tym artykule opisano atrybuty, które można zastosować do właściwości lub innym członkom swojej niestandardowych kontrolek i składników.</span><span class="sxs-lookup"><span data-stu-id="08d5f-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="08d5f-120">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="08d5f-120">Custom Control Painting and Rendering</span></span>](custom-control-painting-and-rendering.md)  
 <span data-ttu-id="08d5f-121">Pokazuje, jak dostosować wygląd kontrolek.</span><span class="sxs-lookup"><span data-stu-id="08d5f-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="08d5f-122">Układ w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08d5f-122">Layout in Windows Forms Controls</span></span>](layout-in-windows-forms-controls.md)  
 <span data-ttu-id="08d5f-123">Pokazuje, jak tworzyć zaawansowane układy formantów i formularze.</span><span class="sxs-lookup"><span data-stu-id="08d5f-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="08d5f-124">Wielowątkowość w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08d5f-124">Multithreading in Windows Forms Controls</span></span>](multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="08d5f-125">Pokazuje, jak zaimplementować formantów wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="08d5f-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="08d5f-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="08d5f-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="08d5f-127">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="08d5f-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="08d5f-128">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="08d5f-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="08d5f-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="08d5f-129">Related Sections</span></span>  
 <span data-ttu-id="08d5f-130">[Atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="08d5f-130">[Design-Time Attributes for Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))</span></span>  
 <span data-ttu-id="08d5f-131">Wyświetla listę atrybutów metadanych, które mają zastosowanie do składników i formantów, aby były wyświetlane poprawnie w czasie projektowania w projektantów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="08d5f-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 <span data-ttu-id="08d5f-132">[Rozszerzenie obsługi w czasie projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="08d5f-132">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>  
 <span data-ttu-id="08d5f-133">Opisuje sposób implementacji klas, takich jak edytorach i projektantach, które zapewniają obsługę projektowania.</span><span class="sxs-lookup"><span data-stu-id="08d5f-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 <span data-ttu-id="08d5f-134">[Instrukcje: Licencja składników i formantów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="08d5f-134">[How to: License Components and Controls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fe8b1eh9(v=vs.120))</span></span>  
 <span data-ttu-id="08d5f-135">Opisuje sposób implementacji licencji w ramach sterowania lub składnika.</span><span class="sxs-lookup"><span data-stu-id="08d5f-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="08d5f-136">Zobacz też [tworzenia kontrolek Windows Forms w czasie projektowania](developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="08d5f-136">Also see [Developing Windows Forms Controls at Design Time](developing-windows-forms-controls-at-design-time.md).</span></span>

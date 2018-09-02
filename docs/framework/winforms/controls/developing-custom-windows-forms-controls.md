---
title: Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 6ab459f37e825d71163e375e10f30fbe3e23911a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397606"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="907da-102">Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="907da-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="907da-103">Kontrolek formularzy Windows Forms są składniki wielokrotnego użytku, hermetyzacji funkcjonalność interfejsu użytkownika, które są używane w aplikacjach opartych na Windows po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="907da-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="907da-104">Nie tylko formularze Windows zapewnia wiele kontrolek gotowych do użycia, również udostępnia infrastrukturę do tworzenia własnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="907da-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="907da-105">Można połączyć istniejące kontrolki, rozszerzanie istniejących kontrolek lub tworzyć własne niestandardowe formanty.</span><span class="sxs-lookup"><span data-stu-id="907da-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="907da-106">Ta sekcja zawiera ogólne informacje i przykłady ułatwiające opracowywanie kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="907da-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="907da-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="907da-107">In This Section</span></span>  
 [<span data-ttu-id="907da-108">Omówienie używania kontrolek w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907da-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="907da-109">Podświetla podstawowe elementy za pomocą formantów w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="907da-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="907da-110">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="907da-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="907da-111">W tym artykule opisano różne rodzaje Kontrolki niestandardowe można tworzyć za pomocą <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="907da-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="907da-112">Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907da-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="907da-113">W tym artykule omówiono pierwszych kroków w tworzeniu formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="907da-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="907da-114">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907da-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="907da-115">Pokazuje, jak dodać do właściwości kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="907da-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="907da-116">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907da-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="907da-117">Pokazuje, jak obsługiwać i definiowania zdarzenia w kontrolkach formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="907da-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="907da-118">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907da-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="907da-119">W tym artykule opisano atrybuty, które można zastosować do właściwości lub innym członkom swojej niestandardowych kontrolek i składników.</span><span class="sxs-lookup"><span data-stu-id="907da-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="907da-120">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="907da-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="907da-121">Pokazuje, jak dostosować wygląd kontrolek.</span><span class="sxs-lookup"><span data-stu-id="907da-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="907da-122">Układ w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907da-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="907da-123">Pokazuje, jak tworzyć zaawansowane układy formantów i formularze.</span><span class="sxs-lookup"><span data-stu-id="907da-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="907da-124">Wielowątkowość w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="907da-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="907da-125">Pokazuje, jak zaimplementować formantów wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="907da-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="907da-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="907da-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="907da-127">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="907da-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="907da-128">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="907da-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="907da-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="907da-129">Related Sections</span></span>  
 [<span data-ttu-id="907da-130">Atrybuty czasu projektowania dla składników</span><span class="sxs-lookup"><span data-stu-id="907da-130">Design-Time Attributes for Components</span></span>](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="907da-131">Wyświetla listę atrybutów metadanych, które mają zastosowanie do składników i formantów, aby były wyświetlane poprawnie w czasie projektowania w projektantów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="907da-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="907da-132">Rozszerzenie obsługi w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="907da-132">Extending Design-Time Support</span></span>](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="907da-133">Opisuje sposób implementacji klas, takich jak edytorach i projektantach, które zapewniają obsługę projektowania.</span><span class="sxs-lookup"><span data-stu-id="907da-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 [<span data-ttu-id="907da-134">Porady: Licencjonowanie składników i kontrolek</span><span class="sxs-lookup"><span data-stu-id="907da-134">How to: License Components and Controls</span></span>](https://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 <span data-ttu-id="907da-135">Opisuje sposób implementacji licencji w ramach sterowania lub składnika.</span><span class="sxs-lookup"><span data-stu-id="907da-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="907da-136">Zobacz też [tworzenia kontrolek Windows Forms w czasie projektowania](https://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="907da-136">Also see [Developing Windows Forms Controls at Design Time](https://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span></span>

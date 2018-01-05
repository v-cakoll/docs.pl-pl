---
title: "Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2f15dc4bb3bd4a6d1163823509f0f2c2bf2c11a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="bef29-102">Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bef29-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="bef29-103">Formanty formularzy systemu Windows są składniki wielokrotnego użytku, Hermetyzowanie funkcji interfejsu użytkownika, które są używane w aplikacjach opartych na systemie Windows po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="bef29-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="bef29-104">Nie tylko formularze systemu Windows udostępnia wiele gotowych do użycia formantów, również zapewnia infrastrukturę do tworzenia własnych formantów.</span><span class="sxs-lookup"><span data-stu-id="bef29-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="bef29-105">Można połączyć istniejących formantów, rozszerzanie istniejących formantów lub tworzenie Kontrolki niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="bef29-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="bef29-106">Ta sekcja zawiera informacje i przykłady ułatwiające opracowanie formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bef29-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bef29-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bef29-107">In This Section</span></span>  
 [<span data-ttu-id="bef29-108">Omówienie używania kontrolek w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef29-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="bef29-109">Zawiera opis podstawowych elementów za pomocą formantów w aplikacjach formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bef29-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="bef29-110">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="bef29-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="bef29-111">W tym artykule opisano różne rodzaje Kontrolki niestandardowe można tworzyć z <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bef29-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="bef29-112">Podstawowe informacje o opracowywaniu kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef29-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="bef29-113">W tym artykule omówiono pierwszym krokiem tworzenia kontrolki formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bef29-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="bef29-114">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef29-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="bef29-115">Przedstawiono sposób dodawania do właściwości formantów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bef29-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="bef29-116">Zdarzenia w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef29-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="bef29-117">Przedstawia sposób obsługi i definiowanie zdarzeń w formantach formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="bef29-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="bef29-118">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef29-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="bef29-119">Zawiera opis atrybutów, które można zastosować do właściwości lub innych elementach członkowskich niestandardowe formanty i składniki.</span><span class="sxs-lookup"><span data-stu-id="bef29-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="bef29-120">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="bef29-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="bef29-121">Pokazuje, jak dostosować wygląd formantów.</span><span class="sxs-lookup"><span data-stu-id="bef29-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="bef29-122">Układ w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef29-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="bef29-123">Przedstawia sposób tworzenia zaawansowanych układów dla formantów i formularze.</span><span class="sxs-lookup"><span data-stu-id="bef29-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="bef29-124">Wielowątkowość w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bef29-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="bef29-125">Przedstawia sposób wdrożenia formantów wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="bef29-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bef29-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="bef29-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="bef29-127">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="bef29-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="bef29-128">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="bef29-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bef29-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bef29-129">Related Sections</span></span>  
 [<span data-ttu-id="bef29-130">Atrybuty czasu projektowania dla składników</span><span class="sxs-lookup"><span data-stu-id="bef29-130">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="bef29-131">Wyświetla listę atrybutów metadanych do zastosowania do składników i formantów, dzięki czemu są wyświetlane poprawnie w czasie projektowania w wizualnych projektantów.</span><span class="sxs-lookup"><span data-stu-id="bef29-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="bef29-132">Rozszerzenie obsługi w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="bef29-132">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="bef29-133">Zawiera opis sposobu implementacji klasy, takie jak edytory i projektantów, które zapewniają obsługę w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="bef29-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 [<span data-ttu-id="bef29-134">Porady: licencja składników i formantów</span><span class="sxs-lookup"><span data-stu-id="bef29-134">How to: License Components and Controls</span></span>](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 <span data-ttu-id="bef29-135">Opisuje sposób wdrożenia licencjonowania w kontroli lub składnika.</span><span class="sxs-lookup"><span data-stu-id="bef29-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="bef29-136">Zobacz też [opracowywanie formantów formularzy systemu Windows w czasie projektowania](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="bef29-136">Also see [Developing Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span></span>

---
title: COM Interop (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87c87852024412b7a7ed55a2c429842ce75a13a8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="00720-102">COM Interop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00720-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="00720-103">Składnik modelu COM. pozwala obiektu do udostępnienia jej funkcji do innych składników i umożliwia obsługę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00720-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="00720-104">Większość oprogramowania współczesnych obejmuje obiekty COM.</span><span class="sxs-lookup"><span data-stu-id="00720-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="00720-105">Mimo że zestawy .NET to najlepszy wybór dla nowych aplikacji, w czasie konieczne może być zastosowana obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="00720-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="00720-106">W tej sekcji opisano niektóre problemy związane z tworzenie i używanie obiektów COM z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00720-106">This section covers some of the issues associated with creating and using COM objects with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00720-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="00720-107">In This Section</span></span>  
 [<span data-ttu-id="00720-108">Wprowadzenie do COM Interop</span><span class="sxs-lookup"><span data-stu-id="00720-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="00720-109">Przegląd współdziałania COM.</span><span class="sxs-lookup"><span data-stu-id="00720-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="00720-110">Porady: odwoływać się do obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00720-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="00720-111">Uwzględniono również sposób dodawania odwołania do obiektów COM, które mają biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="00720-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="00720-112">Porady: Praca z kontrolkami ActiveX</span><span class="sxs-lookup"><span data-stu-id="00720-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="00720-113">Pokazuje, jak używać istniejących formantów ActiveX do dodawania funkcji do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] przybornika.</span><span class="sxs-lookup"><span data-stu-id="00720-113">Demonstrates how to use existing ActiveX controls to add features to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Toolbox.</span></span>  
  
 [<span data-ttu-id="00720-114">Wskazówki: Wywoływanie Windows API</span><span class="sxs-lookup"><span data-stu-id="00720-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="00720-115">Przeprowadza użytkownika przez proces wywoływania interfejsów API, które są częścią systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="00720-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="00720-116">Porady: wywoływanie Windows API</span><span class="sxs-lookup"><span data-stu-id="00720-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="00720-117">Pokazuje, jak zdefiniować i Wywołaj `MessageBox` funkcji w User32.dll.</span><span class="sxs-lookup"><span data-stu-id="00720-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="00720-118">Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="00720-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="00720-119">Demonstracja wywoływania funkcji systemu Windows, który ma parametr typu bez znaku.</span><span class="sxs-lookup"><span data-stu-id="00720-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="00720-120">Wskazówki: Tworzenie obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00720-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="00720-121">Przeprowadza użytkownika przez proces tworzenia obiektów COM z włączonymi i wyłączonymi szablonu klasy COM.</span><span class="sxs-lookup"><span data-stu-id="00720-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="00720-122">Problemów związanych ze współdziałaniem</span><span class="sxs-lookup"><span data-stu-id="00720-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="00720-123">Obejmuje niektóre problemy, które można napotkać, korzystając z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="00720-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="00720-124">Współdziałanie COM w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00720-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="00720-125">Zawiera omówienie sposobu użycia obiekty COM i .NET Framework w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="00720-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="00720-126">Wskazówki: Wdrażanie dziedziczenia z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="00720-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="00720-127">Zawiera opis używania istniejących obiektów COM jako podstawa dla nowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="00720-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="00720-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="00720-128">Related Sections</span></span>  
 [<span data-ttu-id="00720-129">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="00720-129">Interoperating with Unmanaged Code</span></span>](https://msdn.microsoft.com/library/sd10k43k)  
 <span data-ttu-id="00720-130">Opisuje współdziałanie usług świadczonych przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="00720-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="00720-131">Udostępnianie składników modelu COM aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00720-131">Exposing COM Components to the .NET Framework</span></span>](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="00720-132">W tym artykule opisano proces wywoływania typów COM za pomocą modelu COM interop.</span><span class="sxs-lookup"><span data-stu-id="00720-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="00720-133">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="00720-133">Exposing .NET Framework Components to COM</span></span>](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="00720-134">Zawiera opis przygotowania i stosowania typy zarządzane z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="00720-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="00720-135">Stosowanie atrybutów międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="00720-135">Applying Interop Attributes</span></span>](https://msdn.microsoft.com/library/d4w8x20h)  
 <span data-ttu-id="00720-136">Obejmuje atrybutów używanych podczas pracy z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="00720-136">Covers attributes you can use when working with unmanaged code.</span></span>

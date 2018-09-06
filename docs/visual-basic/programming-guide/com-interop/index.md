---
title: COM Interop (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: b6da65a0c94875f73c8e1094448d76a72823404d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871062"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="8b5b9-102">COM Interop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b5b9-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="8b5b9-103">Component Object Model (COM) umożliwia obiektu do udostępnienia jej funkcjonalność do innych składników oraz obsługi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="8b5b9-104">Większość oprogramowaniu współczesnych zawiera obiekty COM.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="8b5b9-105">Mimo że zestawów .NET są najlepszym wyborem dla nowych aplikacji, czasami konieczne może być zastosowana obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="8b5b9-106">W tej sekcji opisano niektóre zagadnienia związane z tworzeniem i przy użyciu obiektów COM z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b5b9-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8b5b9-107">In This Section</span></span>  
 [<span data-ttu-id="8b5b9-108">Wprowadzenie do usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="8b5b9-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="8b5b9-109">Przegląd współdziałania COM.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="8b5b9-110">Porady: odwołania do obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b5b9-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="8b5b9-111">Opisano, jak dodać odwołania do obiektów COM, które mają bibliotek typów.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="8b5b9-112">Instrukcje: praca z kontrolkami ActiveX</span><span class="sxs-lookup"><span data-stu-id="8b5b9-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="8b5b9-113">Pokazuje, jak dodać funkcje do przybornika Visual Studio za pomocą istniejących formantów ActiveX.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="8b5b9-114">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8b5b9-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="8b5b9-115">Przeprowadzi Cię przez proces wywoływania interfejsów API, które są częścią tego systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="8b5b9-116">Instrukcje: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8b5b9-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="8b5b9-117">Pokazuje, jak definiować i wywoływać `MessageBox` funkcji w bibliotece User32.dll.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="8b5b9-118">Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="8b5b9-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="8b5b9-119">Pokazuje sposób wywołania funkcji Windows, która ma parametr typu bez znaku.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="8b5b9-120">Wskazówki: Tworzenie obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b5b9-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="8b5b9-121">Przeprowadzi Cię przez proces tworzenia obiektów COM z lub bez szablonu klasy COM.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="8b5b9-122">Rozwiązywanie problemów związanych z współdziałaniem</span><span class="sxs-lookup"><span data-stu-id="8b5b9-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="8b5b9-123">Obejmuje niektóre problemy, które można napotkać podczas za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="8b5b9-124">Współdziałanie COM w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8b5b9-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="8b5b9-125">Zawiera omówienie sposobu użycia obiekty COM i .NET Framework w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="8b5b9-126">Przewodnik: wdrażanie dziedziczenia z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="8b5b9-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="8b5b9-127">W tym artykule opisano, przy użyciu istniejących obiektów COM jako podstawy dla nowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b5b9-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="8b5b9-128">Related Sections</span></span>  
 [<span data-ttu-id="8b5b9-129">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="8b5b9-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="8b5b9-130">Opisuje współdziałanie usługi udostępniane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="8b5b9-131">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8b5b9-131">Exposing COM Components to the .NET Framework</span></span>](https://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="8b5b9-132">W tym artykule opisano proces typy modelu COM za pomocą współdziałania z modelem COM podczas wywoływania.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="8b5b9-133">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="8b5b9-133">Exposing .NET Framework Components to COM</span></span>](https://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="8b5b9-134">W tym artykule opisano przygotowania i korzystanie z typami zarządzanymi z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="8b5b9-135">Stosowanie atrybutów międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="8b5b9-135">Applying Interop Attributes</span></span>](../../../framework/interop/applying-interop-attributes.md)  
 <span data-ttu-id="8b5b9-136">Opisano atrybuty, których można użyć podczas pracy z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="8b5b9-136">Covers attributes you can use when working with unmanaged code.</span></span>

---
title: COM Interop (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: 1bcfba25c86c46f986c061241a5d09f9aaa6d248
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627081"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="bbedd-102">COM Interop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbedd-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="bbedd-103">Component Object Model (COM) umożliwia obiektowi uwidocznienie jego funkcjonalności innym składnikom i hostowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbedd-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="bbedd-104">Większość współczesnych oprogramowania obejmuje obiekty COM.</span><span class="sxs-lookup"><span data-stu-id="bbedd-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="bbedd-105">Chociaż zestawy .NET najlepiej sprawdzają się w przypadku nowych aplikacji, może być konieczne korzystanie z obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="bbedd-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="bbedd-106">W tej sekcji omówiono niektóre problemy związane z tworzeniem i korzystaniem z obiektów COM przy użyciu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bbedd-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bbedd-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bbedd-107">In This Section</span></span>  
 [<span data-ttu-id="bbedd-108">Wprowadzenie do usługi międzyoperacyjnej modelu COM</span><span class="sxs-lookup"><span data-stu-id="bbedd-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="bbedd-109">Zawiera omówienie współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="bbedd-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="bbedd-110">Instrukcje: Odwołuje się do obiektów COM z Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bbedd-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="bbedd-111">Opisuje sposób dodawania odwołań do obiektów COM z bibliotekami typów.</span><span class="sxs-lookup"><span data-stu-id="bbedd-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="bbedd-112">Instrukcje: praca z kontrolkami ActiveX</span><span class="sxs-lookup"><span data-stu-id="bbedd-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="bbedd-113">Pokazuje, jak używać istniejących kontrolek ActiveX do dodawania funkcji do przybornika programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bbedd-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="bbedd-114">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bbedd-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="bbedd-115">Przeprowadzi Cię przez proces wywoływania interfejsów API, które są częścią systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="bbedd-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="bbedd-116">Instrukcje: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bbedd-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="bbedd-117">Pokazuje, jak definiować i wywoływać `MessageBox` funkcję w User32. dll.</span><span class="sxs-lookup"><span data-stu-id="bbedd-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="bbedd-118">Instrukcje: wywoływanie funkcji systemu Windows wykorzystującej typy bez znaku</span><span class="sxs-lookup"><span data-stu-id="bbedd-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="bbedd-119">Pokazuje, jak wywołać funkcję systemu Windows, która ma parametr typu bez znaku.</span><span class="sxs-lookup"><span data-stu-id="bbedd-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="bbedd-120">Przewodnik: Tworzenie obiektów COM przy użyciu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bbedd-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="bbedd-121">Przeprowadzi Cię przez proces tworzenia obiektów COM z szablonem klasy COM i bez niego.</span><span class="sxs-lookup"><span data-stu-id="bbedd-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="bbedd-122">Rozwiązywanie problemów związanych z współdziałaniem</span><span class="sxs-lookup"><span data-stu-id="bbedd-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="bbedd-123">Obejmuje niektóre problemy, które mogą wystąpić podczas korzystania z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="bbedd-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="bbedd-124">Współdziałanie COM w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bbedd-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="bbedd-125">Zawiera omówienie sposobów korzystania z obiektów COM i .NET Framework obiektów w tej samej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbedd-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="bbedd-126">Przewodnik: implementowanie dziedziczenia z obiektami COM</span><span class="sxs-lookup"><span data-stu-id="bbedd-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="bbedd-127">Opisuje używanie istniejących obiektów COM jako podstawy dla nowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="bbedd-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bbedd-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bbedd-128">Related Sections</span></span>  
 [<span data-ttu-id="bbedd-129">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="bbedd-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="bbedd-130">Opisuje usługi współdziałania udostępniane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="bbedd-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="bbedd-131">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bbedd-131">Exposing COM Components to the .NET Framework</span></span>](../../../framework/interop/exposing-com-components.md)  
 <span data-ttu-id="bbedd-132">Opisuje proces wywoływania typów COM za pomocą międzyoperacyjności modelu COM.</span><span class="sxs-lookup"><span data-stu-id="bbedd-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="bbedd-133">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="bbedd-133">Exposing .NET Framework Components to COM</span></span>](../../../framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="bbedd-134">Opisuje przygotowanie i użycie typów zarządzanych z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="bbedd-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="bbedd-135">Stosowanie atrybutów międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="bbedd-135">Applying Interop Attributes</span></span>](../../../standard/native-interop/apply-interop-attributes.md)  
 <span data-ttu-id="bbedd-136">Obejmuje atrybuty, których można używać podczas pracy z niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="bbedd-136">Covers attributes you can use when working with unmanaged code.</span></span>

---
title: Współdziałanie z kodem niezarządzanym
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: cdd8d2781331956289d2b74162e653ba1ee8fad6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114240"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="e6df3-102">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="e6df3-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="e6df3-103">.NET Framework promuje interakcje ze składnikami COM, usługami COM+, bibliotekami typów zewnętrznych i wieloma usługami systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e6df3-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="e6df3-104">Typy danych, sygnatury metod i mechanizmy obsługi błędów różnią się między zarządzanymi i niezarządzanymi modelami obiektów.</span><span class="sxs-lookup"><span data-stu-id="e6df3-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="e6df3-105">Aby uprościć współdziałanie między składnikami .NET Framework i niezarządzanym kodem, a w celu ułatwienia ścieżki migracji, środowisko uruchomieniowe języka wspólnego jest ukrywane zarówno w przypadku klientów, jak i serwerów, które różnią się w tych modelach obiektów.</span><span class="sxs-lookup"><span data-stu-id="e6df3-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="e6df3-106">Kod wykonywany w ramach kontroli środowiska uruchomieniowego jest nazywany kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="e6df3-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="e6df3-107">Z kolei kod, który działa poza środowiskiem uruchomieniowym, jest nazywany kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="e6df3-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="e6df3-108">Składniki COM, interfejsy ActiveX i funkcje interfejsu API systemu Windows to przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e6df3-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e6df3-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e6df3-109">In this section</span></span>

[<span data-ttu-id="e6df3-110">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e6df3-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="e6df3-111">Opisuje, jak używać składników COM z aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6df3-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="e6df3-112">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="e6df3-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="e6df3-113">Opisuje, jak używać składników .NET Framework z aplikacji COM.</span><span class="sxs-lookup"><span data-stu-id="e6df3-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="e6df3-114">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="e6df3-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="e6df3-115">Opisuje sposób wywoływania niezarządzanych funkcji DLL przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="e6df3-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="e6df3-116">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="e6df3-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="e6df3-117">Opisuje kierowanie dla międzyoperacyjności modelu COM i wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="e6df3-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="e6df3-118">Instrukcje: Mapowanie wyników HRESULT i wyjątków</span><span class="sxs-lookup"><span data-stu-id="e6df3-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="e6df3-119">Opisuje mapowanie między wyjątkami i WYNIKami HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e6df3-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="e6df3-120">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="e6df3-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="e6df3-121">Opisuje otoki udostępniane przez międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e6df3-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="e6df3-122">Równoważność typów i osadzone typy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="e6df3-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="e6df3-123">Opisuje, jak informacje o typie dla typów COM są osadzone w zestawach oraz jak środowisko uruchomieniowe języka wspólnego określa równoważność osadzonych typów COM.</span><span class="sxs-lookup"><span data-stu-id="e6df3-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="e6df3-124">Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="e6df3-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="e6df3-125">Opisuje sposób tworzenia podstawowych zestawów międzyoperacyjnych za pomocą *Tlbimp. exe* (Importer biblioteki typów).</span><span class="sxs-lookup"><span data-stu-id="e6df3-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="e6df3-126">Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="e6df3-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="e6df3-127">W tym artykule opisano sposób rejestrowania podstawowych zestawów międzyoperacyjnych, zanim będzie można odwołać się do nich w projektach.</span><span class="sxs-lookup"><span data-stu-id="e6df3-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="e6df3-128">Współdziałanie z COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="e6df3-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="e6df3-129">Opisuje sposób, w jaki współdziałanie modelu COM może aktywować składniki bez używania rejestru systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6df3-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="e6df3-130">Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e6df3-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="e6df3-131">Opisuje sposób tworzenia manifestu aplikacji i tworzenia i osadzania manifestu składnika.</span><span class="sxs-lookup"><span data-stu-id="e6df3-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

---
title: Współdziałanie z kodem niezarządzanym
ms.date: 01/17/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 38c569633304ed9e6f86e7a04ef7b0dfa79b6704
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="79ad0-102">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="79ad0-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="79ad0-103">.NET Framework zamienia interakcji z COM składników, COM + usług, bibliotek typu zewnętrznego i wiele usług systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="79ad0-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="79ad0-104">Typy danych, podpisy metod i mechanizmy obsługi błędów różnić modele obiektów zarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="79ad0-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="79ad0-105">Aby uprościć współdziałanie między składników .NET Framework i kodu niezarządzanego i ścieżki migracji do jej obsługi ułatwiają, środowisko uruchomieniowe języka wspólnego zawiera od klientów i serwerów różnice w tych modeli obiektów.</span><span class="sxs-lookup"><span data-stu-id="79ad0-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="79ad0-106">Kod, który wykonuje pod kontrolą środowiska uruchomieniowego jest wywoływana kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="79ad0-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="79ad0-107">Z drugiej strony kod uruchamiany poza środowisko wykonawcze jest nazywany kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="79ad0-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="79ad0-108">Składniki modelu COM, interfejsy ActiveX i funkcji Win32 API są przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="79ad0-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="79ad0-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="79ad0-109">In this section</span></span>

[<span data-ttu-id="79ad0-110">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="79ad0-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="79ad0-111">Informacje dotyczące używania składniki COM w aplikacjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79ad0-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="79ad0-112">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="79ad0-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="79ad0-113">Informacje dotyczące używania składników .NET Framework z aplikacjami COM.</span><span class="sxs-lookup"><span data-stu-id="79ad0-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="79ad0-114">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="79ad0-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="79ad0-115">Opisuje sposób wywoływania niezarządzanego wywołanie funkcji DLL przy użyciu platformy.</span><span class="sxs-lookup"><span data-stu-id="79ad0-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="79ad0-116">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="79ad0-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="79ad0-117">Opisuje, przekazywanie do wywoływania platformy i COM interop.</span><span class="sxs-lookup"><span data-stu-id="79ad0-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="79ad0-118">Instrukcje: Mapowanie wyników HRESULT i wyjątków</span><span class="sxs-lookup"><span data-stu-id="79ad0-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="79ad0-119">Opisuje mapowanie między wyjątki i wyników HRESULT.</span><span class="sxs-lookup"><span data-stu-id="79ad0-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="79ad0-120">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="79ad0-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="79ad0-121">W tym artykule opisano otoki podał COM interop.</span><span class="sxs-lookup"><span data-stu-id="79ad0-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="79ad0-122">Równoważność typów i osadzone typy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="79ad0-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="79ad0-123">Opisuje sposób informacje o typie dla typów COM jest osadzony w zestawach i jak środowisko uruchomieniowe języka wspólnego określa równoważność osadzone typy COM.</span><span class="sxs-lookup"><span data-stu-id="79ad0-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="79ad0-124">Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="79ad0-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="79ad0-125">Opisuje sposób tworzenia podstawowe zestawy międzyoperacyjne przy użyciu *Tlbimp.exe* (Importer biblioteki typów).</span><span class="sxs-lookup"><span data-stu-id="79ad0-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="79ad0-126">Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="79ad0-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="79ad0-127">Opisuje sposób rejestrowania podstawowe zestawy międzyoperacyjne, zanim można odwoływać się je w projektach.</span><span class="sxs-lookup"><span data-stu-id="79ad0-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="79ad0-128">Współdziałanie z COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="79ad0-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="79ad0-129">W tym artykule opisano, jak Usługa międzyoperacyjna modelu COM może aktywować składniki bez za pomocą rejestru systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="79ad0-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="79ad0-130">Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="79ad0-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="79ad0-131">Opisuje sposób tworzenia manifest aplikacji oraz tworzenie i osadzanie manifestu składnika.</span><span class="sxs-lookup"><span data-stu-id="79ad0-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

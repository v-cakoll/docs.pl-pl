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
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457971"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="7852a-102">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="7852a-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="7852a-103">Program .NET Framework promuje interakcję ze składnikami COM, usługami COM+, bibliotekami typów zewnętrznych i wieloma usługami systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7852a-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="7852a-104">Typy danych, podpisy metod i mechanizmy obsługi błędów różnią się w zależności od modeli obiektów zarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="7852a-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="7852a-105">Aby uprościć współdziałanie między składnikami programu .NET Framework i kodem niezarządzanym i ułatwić ścieżkę migracji, środowisko wykonawcze języka wspólnego ukrywa przed klientami i serwerami różnice w tych modelach obiektów.</span><span class="sxs-lookup"><span data-stu-id="7852a-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="7852a-106">Kod, który wykonuje pod kontrolą środowiska wykonawczego jest nazywany kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="7852a-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="7852a-107">Z drugiej strony kod, który działa poza środowisko wykonawcze jest nazywany kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="7852a-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="7852a-108">Składniki COM, interfejsy ActiveX i funkcje interfejsu API systemu Windows są przykładami niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="7852a-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7852a-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7852a-109">In this section</span></span>

[<span data-ttu-id="7852a-110">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7852a-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="7852a-111">W tym artykule opisano sposób używania składników COM z aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7852a-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="7852a-112">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="7852a-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="7852a-113">W tym artykule opisano sposób używania składników .NET Framework z aplikacji COM.</span><span class="sxs-lookup"><span data-stu-id="7852a-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="7852a-114">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="7852a-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="7852a-115">W tym artykule opisano sposób wywoływania niezarządzanych funkcji DLL przy użyciu platformy wywołać.</span><span class="sxs-lookup"><span data-stu-id="7852a-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="7852a-116">Organizowanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="7852a-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="7852a-117">Opisuje kierowanie dla com interop i platformy wywołać.</span><span class="sxs-lookup"><span data-stu-id="7852a-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="7852a-118">Porady: mapowanie wyników HRESULT i wyjątków</span><span class="sxs-lookup"><span data-stu-id="7852a-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="7852a-119">Opisuje mapowanie między wyjątkami i HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="7852a-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="7852a-120">Równoważność typów i osadzone typy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="7852a-120">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="7852a-121">W tym artykule opisano, jak informacje o typie dla typów COM są osadzane w zestawach i jak środowisko uruchomieniowe języka wspólnego określa równoważność osadzonych typów COM.</span><span class="sxs-lookup"><span data-stu-id="7852a-121">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="7852a-122">Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="7852a-122">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="7852a-123">W tym artykule opisano sposób tworzenia podstawowych zestawów międzyoperacyjnych przy użyciu *programu Tlbimp.exe* (importer biblioteki typów).</span><span class="sxs-lookup"><span data-stu-id="7852a-123">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="7852a-124">Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="7852a-124">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="7852a-125">W tym artykule opisano sposób rejestrowania podstawowych zestawów międzyoperacyjnych, zanim będzie można odwoływać się do nich w projektach.</span><span class="sxs-lookup"><span data-stu-id="7852a-125">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="7852a-126">Współdziałanie z COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="7852a-126">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="7852a-127">W tym artykule opisano, jak com interop można aktywować składniki bez korzystania z rejestru systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7852a-127">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="7852a-128">Instrukcje: Konfigurowanie aktywacji bez rejestracji składników COM opartych na platformie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7852a-128">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="7852a-129">W tym artykule opisano sposób tworzenia manifestu aplikacji oraz sposobu tworzenia i osadzania manifestu składnika.</span><span class="sxs-lookup"><span data-stu-id="7852a-129">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7852a-130">Powiązane sekcje</span><span class="sxs-lookup"><span data-stu-id="7852a-130">Related sections</span></span>

[<span data-ttu-id="7852a-131">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="7852a-131">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="7852a-132">Opisuje otoki dostarczone przez współdziałanie COM.</span><span class="sxs-lookup"><span data-stu-id="7852a-132">Describes the wrappers provided by COM interop.</span></span>

---
title: Współdziałanie z kodem niezarządzanym
ms.date: 01/17/2018
helpviewer_keywords:
  - 'unmanaged code, interoperation'
  - 'managed code, interoperation with unmanaged code'
  - '.NET Framework, interoperation with unmanaged code'
  - unmanaged code
  - interoperation with unmanaged code
  - 'interoperation with unmanaged code, about interoperation'
  - 'components [.NET Framework], interoperation with unmanaged code'
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
author: rpetrusha
ms.author: ronpet
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="1049b-102">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="1049b-102">Interoperating with unmanaged code</span></span>

<span data-ttu-id="1049b-103">.NET Framework wspiera interakcji z modelu COM składników modelu COM + usług, zewnętrzne biblioteki typów i wielu usług systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1049b-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="1049b-104">Typy danych, podpisy metod i mechanizmy obsługi błędów różnią się między modele obiektów zarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="1049b-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="1049b-105">Aby uprościć współdziałanie składników .NET Framework, a kod niezarządzany i jej obsługi ułatwiają realizację ścieżki migracji, środowisko uruchomieniowe języka wspólnego zawiera z klientów i serwerów różnice w tych modeli obiektów.</span><span class="sxs-lookup"><span data-stu-id="1049b-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="1049b-106">Kod wykonujący pod kontrolą środowiska wykonawczego jest nazywany kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="1049b-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="1049b-107">Z drugiej strony kod, który działa poza środowisko uruchomieniowe jest nazywany kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="1049b-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="1049b-108">Składniki COM, interfejsów ActiveX i funkcje Windows API są przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="1049b-108">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1049b-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1049b-109">In this section</span></span>

[<span data-ttu-id="1049b-110">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1049b-110">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="1049b-111">Opisuje sposób używania składników COM w aplikacjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1049b-111">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="1049b-112">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="1049b-112">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="1049b-113">Opisuje sposób używania składników .NET Framework z aplikacjami COM.</span><span class="sxs-lookup"><span data-stu-id="1049b-113">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="1049b-114">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="1049b-114">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="1049b-115">W tym artykule opisano sposób wywoływania niezarządzanego wywoływanie funkcji DLL za pomocą platformy.</span><span class="sxs-lookup"><span data-stu-id="1049b-115">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="1049b-116">Marshaling międzyoperacyjny</span><span class="sxs-lookup"><span data-stu-id="1049b-116">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="1049b-117">W tym artykule opisano marshaling dla wywołania COM interop i platformy.</span><span class="sxs-lookup"><span data-stu-id="1049b-117">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="1049b-118">Instrukcje: Mapa wyników HRESULT i wyjątków</span><span class="sxs-lookup"><span data-stu-id="1049b-118">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="1049b-119">Opisuje mapowanie między wyjątków i wartości HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1049b-119">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="1049b-120">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="1049b-120">COM Wrappers</span></span>](com-wrappers.md)  
<span data-ttu-id="1049b-121">W tym artykule opisano otoki, dostarczone przez współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="1049b-121">Describes the wrappers provided by COM interop.</span></span>

[<span data-ttu-id="1049b-122">Równoważność typów i osadzone typy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="1049b-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="1049b-123">W tym artykule opisano, jak informacje o typie dla typów modelu COM jest osadzony w zestawach i jak środowisko uruchomieniowe języka wspólnego określa równoważności typów modelu COM, embedded.</span><span class="sxs-lookup"><span data-stu-id="1049b-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="1049b-124">Instrukcje: Generowanie zestawów podstawowej obsługi Międzyoperacyjnej przy użyciu Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="1049b-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="1049b-125">Opisuje sposób tworzenia podstawowych zestawów międzyoperacyjnych, za pomocą *Tlbimp.exe* (Importer biblioteki typów).</span><span class="sxs-lookup"><span data-stu-id="1049b-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="1049b-126">Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="1049b-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="1049b-127">W tym artykule opisano, jak zarejestrować podstawowe zestawy międzyoperacyjne, zanim można się odwołać je w swoich projektach.</span><span class="sxs-lookup"><span data-stu-id="1049b-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="1049b-128">Współdziałanie z COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="1049b-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="1049b-129">W tym artykule opisano, jak Usługa międzyoperacyjna modelu COM może zostać aktywowany składniki bez za pomocą rejestru Windows.</span><span class="sxs-lookup"><span data-stu-id="1049b-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="1049b-130">Instrukcje: Konfigurowanie składników COM opartych na Framework .NET aktywacji bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="1049b-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="1049b-131">W tym artykule opisano sposób tworzenia manifestu aplikacji oraz jak utworzyć i osadzanie manifestu składnika.</span><span class="sxs-lookup"><span data-stu-id="1049b-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

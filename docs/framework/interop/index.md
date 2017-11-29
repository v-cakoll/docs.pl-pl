---
title: "Współdziałanie z kodem niezarządzanym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2db5b8c2425637e24086f54e8ef69b0e5aac3633
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="db6bb-102">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="db6bb-102">Interoperating with Unmanaged Code</span></span>
<span data-ttu-id="db6bb-103">.NET Framework zamienia interakcji z COM składników, COM + usług, bibliotek typu zewnętrznego i wiele usług systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="db6bb-103">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="db6bb-104">Typy danych, podpisy metod i mechanizmy obsługi błędów różnić modele obiektów zarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="db6bb-104">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="db6bb-105">Aby uprościć współdziałanie między składników .NET Framework i kodu niezarządzanego i ścieżki migracji do jej obsługi ułatwiają, środowisko uruchomieniowe języka wspólnego zawiera od klientów i serwerów różnice w tych modeli obiektów.</span><span class="sxs-lookup"><span data-stu-id="db6bb-105">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>  
  
 <span data-ttu-id="db6bb-106">Kod, który wykonuje pod kontrolą środowiska uruchomieniowego jest wywoływana kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="db6bb-106">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="db6bb-107">Z drugiej strony kod uruchamiany poza środowisko wykonawcze jest nazywany kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="db6bb-107">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="db6bb-108">Składniki modelu COM, interfejsy ActiveX i funkcji Win32 API są przykłady kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="db6bb-108">COM components, ActiveX interfaces, and Win32 API functions are examples of unmanaged code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db6bb-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="db6bb-109">In This Section</span></span>  
 [<span data-ttu-id="db6bb-110">Współdziałanie z kodem niezarządzanym — tematy porad</span><span class="sxs-lookup"><span data-stu-id="db6bb-110">Interoperating with Unmanaged Code How-to Topics</span></span>](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 <span data-ttu-id="db6bb-111">Zawiera łącza do wszystkich — tematy porad znajdującego się w dokumentacji koncepcyjnej na współdziałanie z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="db6bb-111">Provides links to all How-to topics found in the conceptual documentation for interoperating with unmanaged code.</span></span>  
  
 [<span data-ttu-id="db6bb-112">Udostępnianie składników modelu COM aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db6bb-112">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 <span data-ttu-id="db6bb-113">Informacje dotyczące używania składniki COM w aplikacjach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db6bb-113">Describes how to use COM components from .NET Framework applications.</span></span>  
  
 [<span data-ttu-id="db6bb-114">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="db6bb-114">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="db6bb-115">Informacje dotyczące używania składników .NET Framework z aplikacjami COM.</span><span class="sxs-lookup"><span data-stu-id="db6bb-115">Describes how to use .NET Framework components from COM applications.</span></span>  
  
 [<span data-ttu-id="db6bb-116">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="db6bb-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="db6bb-117">Opisuje sposób wywoływania niezarządzanego wywołanie funkcji DLL przy użyciu platformy.</span><span class="sxs-lookup"><span data-stu-id="db6bb-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="db6bb-118">Zagadnienia dotyczące projektowania dla współdziałanie</span><span class="sxs-lookup"><span data-stu-id="db6bb-118">Design Considerations for Interoperation</span></span>](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 <span data-ttu-id="db6bb-119">Porady dotyczące pisania zintegrowane składników COM.</span><span class="sxs-lookup"><span data-stu-id="db6bb-119">Provides tips for writing integrated COM components.</span></span>  
  
 [<span data-ttu-id="db6bb-120">Przekazywanie międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="db6bb-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)  
 <span data-ttu-id="db6bb-121">Opisuje, przekazywanie do wywoływania platformy i COM interop.</span><span class="sxs-lookup"><span data-stu-id="db6bb-121">Describes marshaling for COM interop and platform invoke.</span></span>  
  
 [<span data-ttu-id="db6bb-122">Porady: mapowanie wyników HRESULT i wyjątków</span><span class="sxs-lookup"><span data-stu-id="db6bb-122">How to: Map HRESULTs and Exceptions</span></span>](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 <span data-ttu-id="db6bb-123">Opisuje mapowanie między wyjątki i wyników HRESULT.</span><span class="sxs-lookup"><span data-stu-id="db6bb-123">Describes the mapping between exceptions and HRESULTs.</span></span>  
  
 [<span data-ttu-id="db6bb-124">Współdziałanie za pomocą typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="db6bb-124">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="db6bb-125">Określa zachowanie typów ogólnych w modelu COM interop.</span><span class="sxs-lookup"><span data-stu-id="db6bb-125">Describes the behavior of generic types when used in COM interop.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="db6bb-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="db6bb-126">Related Sections</span></span>  
 [<span data-ttu-id="db6bb-127">Współdziałanie COM zaawansowane</span><span class="sxs-lookup"><span data-stu-id="db6bb-127">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="db6bb-128">Zawiera łącza do dodatkowych informacji o włączenie składniki modelu COM aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db6bb-128">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>

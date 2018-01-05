---
title: "Profilowanie (Niezarządzany wykaz interfejsów API)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], profiling
- unmanaged API reference [.NET Framework], profiling
ms.assetid: 14c68e84-657e-49c2-aa8b-4978dbaf4454
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5583a9b81d81acfca80368ca54d5f97899daa1d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-unmanaged-api-reference"></a><span data-ttu-id="fce8f-102">Profilowanie (Niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="fce8f-102">Profiling (Unmanaged API Reference)</span></span>
<span data-ttu-id="fce8f-103">Interfejsu API profilowania umożliwia profilera można monitorować wykonywania programu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="fce8f-103">The profiling API enables a profiler to monitor a program's execution by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fce8f-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fce8f-104">In This Section</span></span>  
 [<span data-ttu-id="fce8f-105">Omówienie profilowania</span><span class="sxs-lookup"><span data-stu-id="fce8f-105">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
 <span data-ttu-id="fce8f-106">Opis usług i interfejsów, które zapewnia środowiska CLR do obsługi profilowania w środowisku .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fce8f-106">Describes the services and interfaces that the CLR provides to support profiling in the .NET Framework environment.</span></span>  
  
 [<span data-ttu-id="fce8f-107">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="fce8f-107">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 <span data-ttu-id="fce8f-108">W tym artykule opisano niezarządzane interfejsy, które używa interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="fce8f-108">Describes the unmanaged interfaces that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="fce8f-109">Konfigurowanie środowiska profilowania</span><span class="sxs-lookup"><span data-stu-id="fce8f-109">Setting Up a Profiling Environment</span></span>](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)  
 <span data-ttu-id="fce8f-110">Zawiera opis czynności, które należy wykonać, aby profilu aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fce8f-110">Describes the steps you must take to profile a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="fce8f-111">Profilery CLR i aplikacje sklepu Windows Store</span><span class="sxs-lookup"><span data-stu-id="fce8f-111">CLR Profilers and Windows Store Apps</span></span>](../../../../docs/framework/unmanaged-api/profiling/clr-profilers-and-windows-store-apps.md)  
 <span data-ttu-id="fce8f-112">W tym artykule omówiono sposób do portu narzędzi diagnostycznych używające API profilowania CLR działało poprawnie z aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="fce8f-112">Discusses how to port diagnostic tools that consume the CLR Profiling API to work successfully with Windows Store apps.</span></span>  
  
 [<span data-ttu-id="fce8f-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="fce8f-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span></span>](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)  
 <span data-ttu-id="fce8f-114">Dokumenty warunków, w których zwraca wywołanie metody `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span><span class="sxs-lookup"><span data-stu-id="fce8f-114">Documents the conditions under which a method call returns the `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span></span>  
  
 [<span data-ttu-id="fce8f-115">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="fce8f-115">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 <span data-ttu-id="fce8f-116">Opisuje niezarządzane statyczne funkcje globalne, które używa interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="fce8f-116">Describes the unmanaged global static functions that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="fce8f-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fce8f-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 <span data-ttu-id="fce8f-118">W tym artykule opisano niezarządzane wyliczenia, które używa interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="fce8f-118">Describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="fce8f-119">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="fce8f-119">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 <span data-ttu-id="fce8f-120">W tym artykule opisano niezarządzane struktury, których używa interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="fce8f-120">Describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fce8f-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fce8f-121">Related Sections</span></span>  
 [<span data-ttu-id="fce8f-122">Wskazówki: Identyfikowanie problemów z wydajnością</span><span class="sxs-lookup"><span data-stu-id="fce8f-122">Walkthrough: Identifying Performance Problems</span></span>](/visualstudio/profiling/walkthrough-identifying-performance-problems)  
 <span data-ttu-id="fce8f-123">Wyjaśniono, jak za pomocą wbudowanych narzędzi profilowania programu Microsoft Visual Studio 2005 Team System.</span><span class="sxs-lookup"><span data-stu-id="fce8f-123">Explains how to use the built-in profiling tools in the Microsoft Visual Studio 2005 Team System.</span></span> <span data-ttu-id="fce8f-124">Te narzędzia umożliwiają o innym podejściu do przy użyciu interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="fce8f-124">These tools provide an alternative approach to using the profiling API.</span></span>

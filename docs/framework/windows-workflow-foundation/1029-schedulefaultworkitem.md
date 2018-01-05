---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dfa9553c25f607ec25fd968c2e8c6db061fb49dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="c9ff2-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="c9ff2-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c9ff2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c9ff2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9ff2-104">ID</span><span class="sxs-lookup"><span data-stu-id="c9ff2-104">ID</span></span>|<span data-ttu-id="c9ff2-105">1029</span><span class="sxs-lookup"><span data-stu-id="c9ff2-105">1029</span></span>|  
|<span data-ttu-id="c9ff2-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c9ff2-106">Keywords</span></span>|<span data-ttu-id="c9ff2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c9ff2-107">WFRuntime</span></span>|  
|<span data-ttu-id="c9ff2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c9ff2-108">Level</span></span>|<span data-ttu-id="c9ff2-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="c9ff2-109">Verbose</span></span>|  
|<span data-ttu-id="c9ff2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c9ff2-110">Channel</span></span>|<span data-ttu-id="c9ff2-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="c9ff2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9ff2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c9ff2-112">Description</span></span>  
 <span data-ttu-id="c9ff2-113">Wskazuje, że zaplanowano element roboczy FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9ff2-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c9ff2-114">Message</span></span>  
 <span data-ttu-id="c9ff2-115">Zaplanowano element roboczy FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="c9ff2-116">Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9ff2-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c9ff2-117">Details</span></span>  
  
|<span data-ttu-id="c9ff2-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c9ff2-118">Data Item Name</span></span>|<span data-ttu-id="c9ff2-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c9ff2-119">Data Item Type</span></span>|<span data-ttu-id="c9ff2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c9ff2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9ff2-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="c9ff2-121">FaultActivity</span></span>|<span data-ttu-id="c9ff2-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="c9ff2-122">xs:string</span></span>|<span data-ttu-id="c9ff2-123">Nazwa typu działania błędów.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="c9ff2-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c9ff2-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="c9ff2-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="c9ff2-125">xs:string</span></span>|<span data-ttu-id="c9ff2-126">Nazwa wyświetlana działania błędów.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="c9ff2-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c9ff2-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="c9ff2-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="c9ff2-128">xs:string</span></span>|<span data-ttu-id="c9ff2-129">Identyfikator wystąpienia działania błędów.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="c9ff2-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="c9ff2-130">ExceptionActivity</span></span>|<span data-ttu-id="c9ff2-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="c9ff2-131">xs:string</span></span>|<span data-ttu-id="c9ff2-132">Nazwa typu działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c9ff2-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c9ff2-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="c9ff2-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="c9ff2-134">xs:string</span></span>|<span data-ttu-id="c9ff2-135">Nazwa wyświetlana działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c9ff2-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c9ff2-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="c9ff2-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="c9ff2-137">xs:string</span></span>|<span data-ttu-id="c9ff2-138">Identyfikator wystąpienia działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c9ff2-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="c9ff2-139">Exception</span></span>|<span data-ttu-id="c9ff2-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="c9ff2-140">xs:string</span></span>|<span data-ttu-id="c9ff2-141">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="c9ff2-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="c9ff2-142">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c9ff2-142">AppDomain</span></span>|<span data-ttu-id="c9ff2-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="c9ff2-143">xs:string</span></span>|<span data-ttu-id="c9ff2-144">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c9ff2-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

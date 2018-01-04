---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 436a0323fcf4498a1d707f7af9bd8204885fd645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="e925f-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e925f-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e925f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e925f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e925f-104">ID</span><span class="sxs-lookup"><span data-stu-id="e925f-104">ID</span></span>|<span data-ttu-id="e925f-105">1030</span><span class="sxs-lookup"><span data-stu-id="e925f-105">1030</span></span>|  
|<span data-ttu-id="e925f-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e925f-106">Keywords</span></span>|<span data-ttu-id="e925f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e925f-107">WFRuntime</span></span>|  
|<span data-ttu-id="e925f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e925f-108">Level</span></span>|<span data-ttu-id="e925f-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="e925f-109">Verbose</span></span>|  
|<span data-ttu-id="e925f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e925f-110">Channel</span></span>|<span data-ttu-id="e925f-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="e925f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e925f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e925f-112">Description</span></span>  
 <span data-ttu-id="e925f-113">Wskazuje, że element roboczy FaultWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e925f-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e925f-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e925f-114">Message</span></span>  
 <span data-ttu-id="e925f-115">Rozpoczęcie wykonywania elementu roboczego FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e925f-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="e925f-116">Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="e925f-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e925f-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e925f-117">Details</span></span>  
  
|<span data-ttu-id="e925f-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e925f-118">Data Item Name</span></span>|<span data-ttu-id="e925f-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e925f-119">Data Item Type</span></span>|<span data-ttu-id="e925f-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e925f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e925f-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e925f-121">FaultActivity</span></span>|<span data-ttu-id="e925f-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="e925f-122">xs:string</span></span>|<span data-ttu-id="e925f-123">Nazwa typu działania błędów.</span><span class="sxs-lookup"><span data-stu-id="e925f-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e925f-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e925f-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e925f-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="e925f-125">xs:string</span></span>|<span data-ttu-id="e925f-126">Nazwa wyświetlana działania błędów.</span><span class="sxs-lookup"><span data-stu-id="e925f-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e925f-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e925f-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e925f-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="e925f-128">xs:string</span></span>|<span data-ttu-id="e925f-129">Identyfikator wystąpienia działania błędów.</span><span class="sxs-lookup"><span data-stu-id="e925f-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e925f-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e925f-130">ExceptionActivity</span></span>|<span data-ttu-id="e925f-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="e925f-131">xs:string</span></span>|<span data-ttu-id="e925f-132">Nazwa typu działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e925f-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e925f-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e925f-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e925f-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="e925f-134">xs:string</span></span>|<span data-ttu-id="e925f-135">Nazwa wyświetlana działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e925f-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e925f-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e925f-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e925f-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="e925f-137">xs:string</span></span>|<span data-ttu-id="e925f-138">Identyfikator wystąpienia działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e925f-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e925f-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="e925f-139">Exception</span></span>|<span data-ttu-id="e925f-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="e925f-140">xs:string</span></span>|<span data-ttu-id="e925f-141">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="e925f-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e925f-142">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e925f-142">AppDomain</span></span>|<span data-ttu-id="e925f-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="e925f-143">xs:string</span></span>|<span data-ttu-id="e925f-144">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e925f-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

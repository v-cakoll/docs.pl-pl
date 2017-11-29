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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ba1ae69caff2e08da58e824d35341d3781ea8ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="3034d-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="3034d-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3034d-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3034d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3034d-104">ID</span><span class="sxs-lookup"><span data-stu-id="3034d-104">ID</span></span>|<span data-ttu-id="3034d-105">1029</span><span class="sxs-lookup"><span data-stu-id="3034d-105">1029</span></span>|  
|<span data-ttu-id="3034d-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3034d-106">Keywords</span></span>|<span data-ttu-id="3034d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3034d-107">WFRuntime</span></span>|  
|<span data-ttu-id="3034d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="3034d-108">Level</span></span>|<span data-ttu-id="3034d-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="3034d-109">Verbose</span></span>|  
|<span data-ttu-id="3034d-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="3034d-110">Channel</span></span>|<span data-ttu-id="3034d-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="3034d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3034d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3034d-112">Description</span></span>  
 <span data-ttu-id="3034d-113">Wskazuje, że zaplanowano element roboczy FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="3034d-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3034d-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="3034d-114">Message</span></span>  
 <span data-ttu-id="3034d-115">Zaplanowano element roboczy FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3034d-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="3034d-116">Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="3034d-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3034d-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3034d-117">Details</span></span>  
  
|<span data-ttu-id="3034d-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="3034d-118">Data Item Name</span></span>|<span data-ttu-id="3034d-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="3034d-119">Data Item Type</span></span>|<span data-ttu-id="3034d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3034d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3034d-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="3034d-121">FaultActivity</span></span>|<span data-ttu-id="3034d-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="3034d-122">xs:string</span></span>|<span data-ttu-id="3034d-123">Nazwa typu działania błędów.</span><span class="sxs-lookup"><span data-stu-id="3034d-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="3034d-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3034d-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="3034d-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="3034d-125">xs:string</span></span>|<span data-ttu-id="3034d-126">Nazwa wyświetlana działania błędów.</span><span class="sxs-lookup"><span data-stu-id="3034d-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="3034d-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3034d-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="3034d-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="3034d-128">xs:string</span></span>|<span data-ttu-id="3034d-129">Identyfikator wystąpienia działania błędów.</span><span class="sxs-lookup"><span data-stu-id="3034d-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="3034d-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="3034d-130">ExceptionActivity</span></span>|<span data-ttu-id="3034d-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="3034d-131">xs:string</span></span>|<span data-ttu-id="3034d-132">Nazwa typu działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3034d-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3034d-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3034d-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="3034d-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="3034d-134">xs:string</span></span>|<span data-ttu-id="3034d-135">Nazwa wyświetlana działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3034d-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3034d-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3034d-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="3034d-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="3034d-137">xs:string</span></span>|<span data-ttu-id="3034d-138">Identyfikator wystąpienia działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3034d-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="3034d-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="3034d-139">Exception</span></span>|<span data-ttu-id="3034d-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="3034d-140">xs:string</span></span>|<span data-ttu-id="3034d-141">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="3034d-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="3034d-142">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="3034d-142">AppDomain</span></span>|<span data-ttu-id="3034d-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="3034d-143">xs:string</span></span>|<span data-ttu-id="3034d-144">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3034d-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

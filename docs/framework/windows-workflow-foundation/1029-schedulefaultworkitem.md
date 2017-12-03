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
ms.openlocfilehash: 7c2031a86a8d46a51b65e60a63a352c56b1a3a53
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="2a799-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="2a799-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2a799-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2a799-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a799-104">ID</span><span class="sxs-lookup"><span data-stu-id="2a799-104">ID</span></span>|<span data-ttu-id="2a799-105">1029</span><span class="sxs-lookup"><span data-stu-id="2a799-105">1029</span></span>|  
|<span data-ttu-id="2a799-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2a799-106">Keywords</span></span>|<span data-ttu-id="2a799-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2a799-107">WFRuntime</span></span>|  
|<span data-ttu-id="2a799-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2a799-108">Level</span></span>|<span data-ttu-id="2a799-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="2a799-109">Verbose</span></span>|  
|<span data-ttu-id="2a799-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2a799-110">Channel</span></span>|<span data-ttu-id="2a799-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="2a799-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a799-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2a799-112">Description</span></span>  
 <span data-ttu-id="2a799-113">Wskazuje, że zaplanowano element roboczy FaultWorkItem.</span><span class="sxs-lookup"><span data-stu-id="2a799-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a799-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2a799-114">Message</span></span>  
 <span data-ttu-id="2a799-115">Zaplanowano element roboczy FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2a799-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="2a799-116">Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="2a799-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a799-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2a799-117">Details</span></span>  
  
|<span data-ttu-id="2a799-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2a799-118">Data Item Name</span></span>|<span data-ttu-id="2a799-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2a799-119">Data Item Type</span></span>|<span data-ttu-id="2a799-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2a799-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a799-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="2a799-121">FaultActivity</span></span>|<span data-ttu-id="2a799-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a799-122">xs:string</span></span>|<span data-ttu-id="2a799-123">Nazwa typu działania błędów.</span><span class="sxs-lookup"><span data-stu-id="2a799-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="2a799-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2a799-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="2a799-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a799-125">xs:string</span></span>|<span data-ttu-id="2a799-126">Nazwa wyświetlana działania błędów.</span><span class="sxs-lookup"><span data-stu-id="2a799-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="2a799-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2a799-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="2a799-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a799-128">xs:string</span></span>|<span data-ttu-id="2a799-129">Identyfikator wystąpienia działania błędów.</span><span class="sxs-lookup"><span data-stu-id="2a799-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="2a799-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="2a799-130">ExceptionActivity</span></span>|<span data-ttu-id="2a799-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a799-131">xs:string</span></span>|<span data-ttu-id="2a799-132">Nazwa typu działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2a799-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2a799-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2a799-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="2a799-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a799-134">xs:string</span></span>|<span data-ttu-id="2a799-135">Nazwa wyświetlana działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2a799-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2a799-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2a799-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="2a799-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a799-137">xs:string</span></span>|<span data-ttu-id="2a799-138">Identyfikator wystąpienia działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2a799-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="2a799-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="2a799-139">Exception</span></span>|<span data-ttu-id="2a799-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a799-140">xs:string</span></span>|<span data-ttu-id="2a799-141">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="2a799-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="2a799-142">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="2a799-142">AppDomain</span></span>|<span data-ttu-id="2a799-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a799-143">xs:string</span></span>|<span data-ttu-id="2a799-144">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2a799-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

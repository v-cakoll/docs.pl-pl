---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="af09b-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="af09b-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="af09b-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="af09b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af09b-104">ID</span><span class="sxs-lookup"><span data-stu-id="af09b-104">ID</span></span>|<span data-ttu-id="af09b-105">1031</span><span class="sxs-lookup"><span data-stu-id="af09b-105">1031</span></span>|  
|<span data-ttu-id="af09b-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="af09b-106">Keywords</span></span>|<span data-ttu-id="af09b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="af09b-107">WFRuntime</span></span>|  
|<span data-ttu-id="af09b-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="af09b-108">Level</span></span>|<span data-ttu-id="af09b-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="af09b-109">Verbose</span></span>|  
|<span data-ttu-id="af09b-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="af09b-110">Channel</span></span>|<span data-ttu-id="af09b-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="af09b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="af09b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="af09b-112">Description</span></span>  
 <span data-ttu-id="af09b-113">Wskazuje, że element roboczy FaultWorkItem została ukończona.</span><span class="sxs-lookup"><span data-stu-id="af09b-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="af09b-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="af09b-114">Message</span></span>  
 <span data-ttu-id="af09b-115">Ukończono element roboczy FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="af09b-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="af09b-116">Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="af09b-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="af09b-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="af09b-117">Details</span></span>  
  
|<span data-ttu-id="af09b-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="af09b-118">Data Item Name</span></span>|<span data-ttu-id="af09b-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="af09b-119">Data Item Type</span></span>|<span data-ttu-id="af09b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="af09b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="af09b-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="af09b-121">FaultActivity</span></span>|<span data-ttu-id="af09b-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="af09b-122">xs:string</span></span>|<span data-ttu-id="af09b-123">Nazwa typu działania błędów.</span><span class="sxs-lookup"><span data-stu-id="af09b-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="af09b-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="af09b-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="af09b-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="af09b-125">xs:string</span></span>|<span data-ttu-id="af09b-126">Nazwa wyświetlana działania błędów.</span><span class="sxs-lookup"><span data-stu-id="af09b-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="af09b-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="af09b-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="af09b-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="af09b-128">xs:string</span></span>|<span data-ttu-id="af09b-129">Identyfikator wystąpienia działania błędów.</span><span class="sxs-lookup"><span data-stu-id="af09b-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="af09b-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="af09b-130">ExceptionActivity</span></span>|<span data-ttu-id="af09b-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="af09b-131">xs:string</span></span>|<span data-ttu-id="af09b-132">Nazwa typu działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="af09b-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="af09b-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="af09b-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="af09b-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="af09b-134">xs:string</span></span>|<span data-ttu-id="af09b-135">Nazwa wyświetlana działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="af09b-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="af09b-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="af09b-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="af09b-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="af09b-137">xs:string</span></span>|<span data-ttu-id="af09b-138">Identyfikator wystąpienia działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="af09b-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="af09b-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="af09b-139">Exception</span></span>|<span data-ttu-id="af09b-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="af09b-140">xs:string</span></span>|<span data-ttu-id="af09b-141">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="af09b-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="af09b-142">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="af09b-142">AppDomain</span></span>|<span data-ttu-id="af09b-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="af09b-143">xs:string</span></span>|<span data-ttu-id="af09b-144">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="af09b-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

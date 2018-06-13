---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509683"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="b1ce9-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="b1ce9-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b1ce9-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b1ce9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b1ce9-104">ID</span><span class="sxs-lookup"><span data-stu-id="b1ce9-104">ID</span></span>|<span data-ttu-id="b1ce9-105">1030</span><span class="sxs-lookup"><span data-stu-id="b1ce9-105">1030</span></span>|  
|<span data-ttu-id="b1ce9-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b1ce9-106">Keywords</span></span>|<span data-ttu-id="b1ce9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b1ce9-107">WFRuntime</span></span>|  
|<span data-ttu-id="b1ce9-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b1ce9-108">Level</span></span>|<span data-ttu-id="b1ce9-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="b1ce9-109">Verbose</span></span>|  
|<span data-ttu-id="b1ce9-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b1ce9-110">Channel</span></span>|<span data-ttu-id="b1ce9-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="b1ce9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b1ce9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b1ce9-112">Description</span></span>  
 <span data-ttu-id="b1ce9-113">Wskazuje, że element roboczy FaultWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b1ce9-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b1ce9-114">Message</span></span>  
 <span data-ttu-id="b1ce9-115">Rozpoczęcie wykonywania elementu roboczego FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="b1ce9-116">Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b1ce9-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b1ce9-117">Details</span></span>  
  
|<span data-ttu-id="b1ce9-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b1ce9-118">Data Item Name</span></span>|<span data-ttu-id="b1ce9-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b1ce9-119">Data Item Type</span></span>|<span data-ttu-id="b1ce9-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b1ce9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b1ce9-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="b1ce9-121">FaultActivity</span></span>|<span data-ttu-id="b1ce9-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="b1ce9-122">xs:string</span></span>|<span data-ttu-id="b1ce9-123">Nazwa typu działania błędów.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="b1ce9-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b1ce9-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="b1ce9-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="b1ce9-125">xs:string</span></span>|<span data-ttu-id="b1ce9-126">Nazwa wyświetlana działania błędów.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="b1ce9-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b1ce9-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="b1ce9-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="b1ce9-128">xs:string</span></span>|<span data-ttu-id="b1ce9-129">Identyfikator wystąpienia działania błędów.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="b1ce9-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="b1ce9-130">ExceptionActivity</span></span>|<span data-ttu-id="b1ce9-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="b1ce9-131">xs:string</span></span>|<span data-ttu-id="b1ce9-132">Nazwa typu działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b1ce9-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b1ce9-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="b1ce9-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="b1ce9-134">xs:string</span></span>|<span data-ttu-id="b1ce9-135">Nazwa wyświetlana działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b1ce9-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b1ce9-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="b1ce9-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="b1ce9-137">xs:string</span></span>|<span data-ttu-id="b1ce9-138">Identyfikator wystąpienia działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b1ce9-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="b1ce9-139">Exception</span></span>|<span data-ttu-id="b1ce9-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="b1ce9-140">xs:string</span></span>|<span data-ttu-id="b1ce9-141">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="b1ce9-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="b1ce9-142">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b1ce9-142">AppDomain</span></span>|<span data-ttu-id="b1ce9-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="b1ce9-143">xs:string</span></span>|<span data-ttu-id="b1ce9-144">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b1ce9-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

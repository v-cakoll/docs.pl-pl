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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b25dbd5ced96b8e9ca3ef51e4de841a6238d2cbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="f1879-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="f1879-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f1879-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f1879-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1879-104">ID</span><span class="sxs-lookup"><span data-stu-id="f1879-104">ID</span></span>|<span data-ttu-id="f1879-105">1030</span><span class="sxs-lookup"><span data-stu-id="f1879-105">1030</span></span>|  
|<span data-ttu-id="f1879-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f1879-106">Keywords</span></span>|<span data-ttu-id="f1879-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f1879-107">WFRuntime</span></span>|  
|<span data-ttu-id="f1879-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="f1879-108">Level</span></span>|<span data-ttu-id="f1879-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="f1879-109">Verbose</span></span>|  
|<span data-ttu-id="f1879-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="f1879-110">Channel</span></span>|<span data-ttu-id="f1879-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="f1879-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f1879-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f1879-112">Description</span></span>  
 <span data-ttu-id="f1879-113">Wskazuje, że element roboczy FaultWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f1879-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f1879-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="f1879-114">Message</span></span>  
 <span data-ttu-id="f1879-115">Rozpoczęcie wykonywania elementu roboczego FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="f1879-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="f1879-116">Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="f1879-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f1879-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f1879-117">Details</span></span>  
  
|<span data-ttu-id="f1879-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="f1879-118">Data Item Name</span></span>|<span data-ttu-id="f1879-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="f1879-119">Data Item Type</span></span>|<span data-ttu-id="f1879-120">Opis</span><span class="sxs-lookup"><span data-stu-id="f1879-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f1879-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="f1879-121">FaultActivity</span></span>|<span data-ttu-id="f1879-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="f1879-122">xs:string</span></span>|<span data-ttu-id="f1879-123">Nazwa typu działania błędów.</span><span class="sxs-lookup"><span data-stu-id="f1879-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="f1879-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f1879-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="f1879-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="f1879-125">xs:string</span></span>|<span data-ttu-id="f1879-126">Nazwa wyświetlana działania błędów.</span><span class="sxs-lookup"><span data-stu-id="f1879-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="f1879-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f1879-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="f1879-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="f1879-128">xs:string</span></span>|<span data-ttu-id="f1879-129">Identyfikator wystąpienia działania błędów.</span><span class="sxs-lookup"><span data-stu-id="f1879-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="f1879-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="f1879-130">ExceptionActivity</span></span>|<span data-ttu-id="f1879-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="f1879-131">xs:string</span></span>|<span data-ttu-id="f1879-132">Nazwa typu działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f1879-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f1879-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="f1879-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="f1879-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="f1879-134">xs:string</span></span>|<span data-ttu-id="f1879-135">Nazwa wyświetlana działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f1879-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f1879-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="f1879-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="f1879-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="f1879-137">xs:string</span></span>|<span data-ttu-id="f1879-138">Identyfikator wystąpienia działania, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f1879-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="f1879-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="f1879-139">Exception</span></span>|<span data-ttu-id="f1879-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="f1879-140">xs:string</span></span>|<span data-ttu-id="f1879-141">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="f1879-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="f1879-142">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f1879-142">AppDomain</span></span>|<span data-ttu-id="f1879-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="f1879-143">xs:string</span></span>|<span data-ttu-id="f1879-144">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f1879-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

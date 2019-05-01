---
title: 1029 — ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924361"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="81c43-102">1029 — ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="81c43-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="81c43-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="81c43-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81c43-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="81c43-104">ID</span></span>|<span data-ttu-id="81c43-105">1029</span><span class="sxs-lookup"><span data-stu-id="81c43-105">1029</span></span>|  
|<span data-ttu-id="81c43-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="81c43-106">Keywords</span></span>|<span data-ttu-id="81c43-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="81c43-107">WFRuntime</span></span>|  
|<span data-ttu-id="81c43-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="81c43-108">Level</span></span>|<span data-ttu-id="81c43-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="81c43-109">Verbose</span></span>|  
|<span data-ttu-id="81c43-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="81c43-110">Channel</span></span>|<span data-ttu-id="81c43-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="81c43-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="81c43-112">Opis</span><span class="sxs-lookup"><span data-stu-id="81c43-112">Description</span></span>  
 <span data-ttu-id="81c43-113">Wskazuje, że FaultWorkItem została zaplanowana.</span><span class="sxs-lookup"><span data-stu-id="81c43-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="81c43-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="81c43-114">Message</span></span>  
 <span data-ttu-id="81c43-115">FaultWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="81c43-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="81c43-116">Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="81c43-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="81c43-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="81c43-117">Details</span></span>  
  
|<span data-ttu-id="81c43-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="81c43-118">Data Item Name</span></span>|<span data-ttu-id="81c43-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="81c43-119">Data Item Type</span></span>|<span data-ttu-id="81c43-120">Opis</span><span class="sxs-lookup"><span data-stu-id="81c43-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="81c43-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="81c43-121">FaultActivity</span></span>|<span data-ttu-id="81c43-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="81c43-122">xs:string</span></span>|<span data-ttu-id="81c43-123">Nazwa typu aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="81c43-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="81c43-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="81c43-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="81c43-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="81c43-125">xs:string</span></span>|<span data-ttu-id="81c43-126">Nazwa wyświetlana aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="81c43-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="81c43-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="81c43-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="81c43-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="81c43-128">xs:string</span></span>|<span data-ttu-id="81c43-129">Identyfikator wystąpienia aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="81c43-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="81c43-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="81c43-130">ExceptionActivity</span></span>|<span data-ttu-id="81c43-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="81c43-131">xs:string</span></span>|<span data-ttu-id="81c43-132">Nazwa typu działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="81c43-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="81c43-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="81c43-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="81c43-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="81c43-134">xs:string</span></span>|<span data-ttu-id="81c43-135">Nazwa wyświetlana działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="81c43-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="81c43-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="81c43-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="81c43-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="81c43-137">xs:string</span></span>|<span data-ttu-id="81c43-138">Identyfikator wystąpienia działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="81c43-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="81c43-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="81c43-139">Exception</span></span>|<span data-ttu-id="81c43-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="81c43-140">xs:string</span></span>|<span data-ttu-id="81c43-141">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="81c43-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="81c43-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="81c43-142">AppDomain</span></span>|<span data-ttu-id="81c43-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="81c43-143">xs:string</span></span>|<span data-ttu-id="81c43-144">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="81c43-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

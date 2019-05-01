---
title: 1030 — StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924322"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="8b221-102">1030 — StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="8b221-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8b221-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8b221-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b221-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8b221-104">ID</span></span>|<span data-ttu-id="8b221-105">1030</span><span class="sxs-lookup"><span data-stu-id="8b221-105">1030</span></span>|  
|<span data-ttu-id="8b221-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8b221-106">Keywords</span></span>|<span data-ttu-id="8b221-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8b221-107">WFRuntime</span></span>|  
|<span data-ttu-id="8b221-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8b221-108">Level</span></span>|<span data-ttu-id="8b221-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="8b221-109">Verbose</span></span>|  
|<span data-ttu-id="8b221-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8b221-110">Channel</span></span>|<span data-ttu-id="8b221-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8b221-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8b221-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8b221-112">Description</span></span>  
 <span data-ttu-id="8b221-113">Wskazuje, że FaultWorkItem Trwa uruchamianie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8b221-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8b221-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8b221-114">Message</span></span>  
 <span data-ttu-id="8b221-115">Rozpoczynanie wykonywania FaultWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="8b221-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="8b221-116">Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="8b221-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8b221-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8b221-117">Details</span></span>  
  
|<span data-ttu-id="8b221-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8b221-118">Data Item Name</span></span>|<span data-ttu-id="8b221-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8b221-119">Data Item Type</span></span>|<span data-ttu-id="8b221-120">Opis</span><span class="sxs-lookup"><span data-stu-id="8b221-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8b221-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="8b221-121">FaultActivity</span></span>|<span data-ttu-id="8b221-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="8b221-122">xs:string</span></span>|<span data-ttu-id="8b221-123">Nazwa typu aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="8b221-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="8b221-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8b221-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="8b221-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="8b221-125">xs:string</span></span>|<span data-ttu-id="8b221-126">Nazwa wyświetlana aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="8b221-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="8b221-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8b221-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="8b221-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="8b221-128">xs:string</span></span>|<span data-ttu-id="8b221-129">Identyfikator wystąpienia aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="8b221-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="8b221-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="8b221-130">ExceptionActivity</span></span>|<span data-ttu-id="8b221-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="8b221-131">xs:string</span></span>|<span data-ttu-id="8b221-132">Nazwa typu działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8b221-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8b221-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8b221-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="8b221-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="8b221-134">xs:string</span></span>|<span data-ttu-id="8b221-135">Nazwa wyświetlana działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8b221-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8b221-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8b221-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="8b221-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="8b221-137">xs:string</span></span>|<span data-ttu-id="8b221-138">Identyfikator wystąpienia działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8b221-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8b221-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="8b221-139">Exception</span></span>|<span data-ttu-id="8b221-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="8b221-140">xs:string</span></span>|<span data-ttu-id="8b221-141">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="8b221-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="8b221-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8b221-142">AppDomain</span></span>|<span data-ttu-id="8b221-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="8b221-143">xs:string</span></span>|<span data-ttu-id="8b221-144">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8b221-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

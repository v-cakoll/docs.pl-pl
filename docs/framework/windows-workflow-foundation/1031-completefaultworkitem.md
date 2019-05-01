---
title: 1031 — CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008801"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="ae9f2-102">1031 — CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="ae9f2-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ae9f2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ae9f2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae9f2-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="ae9f2-104">ID</span></span>|<span data-ttu-id="ae9f2-105">1031</span><span class="sxs-lookup"><span data-stu-id="ae9f2-105">1031</span></span>|  
|<span data-ttu-id="ae9f2-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ae9f2-106">Keywords</span></span>|<span data-ttu-id="ae9f2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ae9f2-107">WFRuntime</span></span>|  
|<span data-ttu-id="ae9f2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae9f2-108">Level</span></span>|<span data-ttu-id="ae9f2-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="ae9f2-109">Verbose</span></span>|  
|<span data-ttu-id="ae9f2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ae9f2-110">Channel</span></span>|<span data-ttu-id="ae9f2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ae9f2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae9f2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ae9f2-112">Description</span></span>  
 <span data-ttu-id="ae9f2-113">Wskazuje, że FaultWorkItem zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae9f2-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ae9f2-114">Message</span></span>  
 <span data-ttu-id="ae9f2-115">FaultWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="ae9f2-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="ae9f2-116">Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae9f2-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ae9f2-117">Details</span></span>  
  
|<span data-ttu-id="ae9f2-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ae9f2-118">Data Item Name</span></span>|<span data-ttu-id="ae9f2-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ae9f2-119">Data Item Type</span></span>|<span data-ttu-id="ae9f2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ae9f2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae9f2-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="ae9f2-121">FaultActivity</span></span>|<span data-ttu-id="ae9f2-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae9f2-122">xs:string</span></span>|<span data-ttu-id="ae9f2-123">Nazwa typu aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="ae9f2-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ae9f2-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="ae9f2-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae9f2-125">xs:string</span></span>|<span data-ttu-id="ae9f2-126">Nazwa wyświetlana aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="ae9f2-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ae9f2-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="ae9f2-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae9f2-128">xs:string</span></span>|<span data-ttu-id="ae9f2-129">Identyfikator wystąpienia aktywności błędów.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="ae9f2-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="ae9f2-130">ExceptionActivity</span></span>|<span data-ttu-id="ae9f2-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae9f2-131">xs:string</span></span>|<span data-ttu-id="ae9f2-132">Nazwa typu działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ae9f2-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ae9f2-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="ae9f2-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae9f2-134">xs:string</span></span>|<span data-ttu-id="ae9f2-135">Nazwa wyświetlana działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ae9f2-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ae9f2-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="ae9f2-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae9f2-137">xs:string</span></span>|<span data-ttu-id="ae9f2-138">Identyfikator wystąpienia działania, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ae9f2-139">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="ae9f2-139">Exception</span></span>|<span data-ttu-id="ae9f2-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae9f2-140">xs:string</span></span>|<span data-ttu-id="ae9f2-141">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="ae9f2-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="ae9f2-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ae9f2-142">AppDomain</span></span>|<span data-ttu-id="ae9f2-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae9f2-143">xs:string</span></span>|<span data-ttu-id="ae9f2-144">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ae9f2-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

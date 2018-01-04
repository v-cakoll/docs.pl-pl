---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a80406ce56000703555f7834714222e03d2b65f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="52289-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="52289-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="52289-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="52289-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52289-104">ID</span><span class="sxs-lookup"><span data-stu-id="52289-104">ID</span></span>|<span data-ttu-id="52289-105">1014</span><span class="sxs-lookup"><span data-stu-id="52289-105">1014</span></span>|  
|<span data-ttu-id="52289-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="52289-106">Keywords</span></span>|<span data-ttu-id="52289-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="52289-107">WFRuntime</span></span>|  
|<span data-ttu-id="52289-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="52289-108">Level</span></span>|<span data-ttu-id="52289-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="52289-109">Verbose</span></span>|  
|<span data-ttu-id="52289-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="52289-110">Channel</span></span>|<span data-ttu-id="52289-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="52289-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="52289-112">Opis</span><span class="sxs-lookup"><span data-stu-id="52289-112">Description</span></span>  
 <span data-ttu-id="52289-113">Wskazuje, że zaplanowano element roboczy CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="52289-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="52289-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="52289-114">Message</span></span>  
 <span data-ttu-id="52289-115">Zaplanowano element roboczy CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="52289-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="52289-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="52289-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="52289-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="52289-117">Details</span></span>  
  
|<span data-ttu-id="52289-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="52289-118">Data Item Name</span></span>|<span data-ttu-id="52289-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="52289-119">Data Item Type</span></span>|<span data-ttu-id="52289-120">Opis</span><span class="sxs-lookup"><span data-stu-id="52289-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="52289-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="52289-121">ParentActivity</span></span>|<span data-ttu-id="52289-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="52289-122">xs:string</span></span>|<span data-ttu-id="52289-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="52289-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="52289-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="52289-124">ParentDisplayName</span></span>|<span data-ttu-id="52289-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="52289-125">xs:string</span></span>|<span data-ttu-id="52289-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="52289-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="52289-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="52289-127">ParentInstanceId</span></span>|<span data-ttu-id="52289-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="52289-128">xs:string</span></span>|<span data-ttu-id="52289-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="52289-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="52289-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="52289-130">CompletedActivity</span></span>|<span data-ttu-id="52289-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="52289-131">xs:string</span></span>|<span data-ttu-id="52289-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="52289-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="52289-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="52289-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="52289-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="52289-134">xs:string</span></span>|<span data-ttu-id="52289-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="52289-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="52289-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="52289-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="52289-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="52289-137">xs:string</span></span>|<span data-ttu-id="52289-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="52289-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="52289-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="52289-139">AppDomain</span></span>|<span data-ttu-id="52289-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="52289-140">xs:string</span></span>|<span data-ttu-id="52289-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="52289-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

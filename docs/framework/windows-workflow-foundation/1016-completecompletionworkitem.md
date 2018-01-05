---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f9b09001212de6d5aa4f5fde577b9eeb9d967ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="c3de0-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="c3de0-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c3de0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3de0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3de0-104">ID</span><span class="sxs-lookup"><span data-stu-id="c3de0-104">ID</span></span>|<span data-ttu-id="c3de0-105">1016</span><span class="sxs-lookup"><span data-stu-id="c3de0-105">1016</span></span>|  
|<span data-ttu-id="c3de0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c3de0-106">Keywords</span></span>|<span data-ttu-id="c3de0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c3de0-107">WFRuntime</span></span>|  
|<span data-ttu-id="c3de0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3de0-108">Level</span></span>|<span data-ttu-id="c3de0-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="c3de0-109">Verbose</span></span>|  
|<span data-ttu-id="c3de0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c3de0-110">Channel</span></span>|<span data-ttu-id="c3de0-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="c3de0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3de0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c3de0-112">Description</span></span>  
 <span data-ttu-id="c3de0-113">Wskazuje, że element roboczy CompletionWorkItem została ukończona.</span><span class="sxs-lookup"><span data-stu-id="c3de0-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3de0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c3de0-114">Message</span></span>  
 <span data-ttu-id="c3de0-115">Ukończono element roboczy CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c3de0-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="c3de0-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="c3de0-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3de0-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c3de0-117">Details</span></span>  
  
|<span data-ttu-id="c3de0-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c3de0-118">Data Item Name</span></span>|<span data-ttu-id="c3de0-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c3de0-119">Data Item Type</span></span>|<span data-ttu-id="c3de0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c3de0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3de0-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3de0-121">ParentActivity</span></span>|<span data-ttu-id="c3de0-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="c3de0-122">xs:string</span></span>|<span data-ttu-id="c3de0-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c3de0-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="c3de0-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="c3de0-124">ParentDisplayName</span></span>|<span data-ttu-id="c3de0-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="c3de0-125">xs:string</span></span>|<span data-ttu-id="c3de0-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c3de0-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="c3de0-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="c3de0-127">ParentInstanceId</span></span>|<span data-ttu-id="c3de0-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="c3de0-128">xs:string</span></span>|<span data-ttu-id="c3de0-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c3de0-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="c3de0-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="c3de0-130">CompletedActivity</span></span>|<span data-ttu-id="c3de0-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="c3de0-131">xs:string</span></span>|<span data-ttu-id="c3de0-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="c3de0-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="c3de0-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c3de0-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="c3de0-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="c3de0-134">xs:string</span></span>|<span data-ttu-id="c3de0-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="c3de0-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="c3de0-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c3de0-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="c3de0-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="c3de0-137">xs:string</span></span>|<span data-ttu-id="c3de0-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="c3de0-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="c3de0-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c3de0-139">AppDomain</span></span>|<span data-ttu-id="c3de0-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="c3de0-140">xs:string</span></span>|<span data-ttu-id="c3de0-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c3de0-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

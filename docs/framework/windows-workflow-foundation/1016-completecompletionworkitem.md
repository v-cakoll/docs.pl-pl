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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a7c6b6060e8dd3256d23db7350299d2670f6caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="03e95-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="03e95-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="03e95-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="03e95-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03e95-104">ID</span><span class="sxs-lookup"><span data-stu-id="03e95-104">ID</span></span>|<span data-ttu-id="03e95-105">1016</span><span class="sxs-lookup"><span data-stu-id="03e95-105">1016</span></span>|  
|<span data-ttu-id="03e95-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="03e95-106">Keywords</span></span>|<span data-ttu-id="03e95-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="03e95-107">WFRuntime</span></span>|  
|<span data-ttu-id="03e95-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="03e95-108">Level</span></span>|<span data-ttu-id="03e95-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="03e95-109">Verbose</span></span>|  
|<span data-ttu-id="03e95-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="03e95-110">Channel</span></span>|<span data-ttu-id="03e95-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="03e95-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03e95-112">Opis</span><span class="sxs-lookup"><span data-stu-id="03e95-112">Description</span></span>  
 <span data-ttu-id="03e95-113">Wskazuje, że element roboczy CompletionWorkItem została ukończona.</span><span class="sxs-lookup"><span data-stu-id="03e95-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03e95-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="03e95-114">Message</span></span>  
 <span data-ttu-id="03e95-115">Ukończono element roboczy CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="03e95-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="03e95-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="03e95-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03e95-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="03e95-117">Details</span></span>  
  
|<span data-ttu-id="03e95-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="03e95-118">Data Item Name</span></span>|<span data-ttu-id="03e95-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="03e95-119">Data Item Type</span></span>|<span data-ttu-id="03e95-120">Opis</span><span class="sxs-lookup"><span data-stu-id="03e95-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="03e95-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="03e95-121">ParentActivity</span></span>|<span data-ttu-id="03e95-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="03e95-122">xs:string</span></span>|<span data-ttu-id="03e95-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="03e95-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="03e95-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="03e95-124">ParentDisplayName</span></span>|<span data-ttu-id="03e95-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="03e95-125">xs:string</span></span>|<span data-ttu-id="03e95-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="03e95-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="03e95-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="03e95-127">ParentInstanceId</span></span>|<span data-ttu-id="03e95-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="03e95-128">xs:string</span></span>|<span data-ttu-id="03e95-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="03e95-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="03e95-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="03e95-130">CompletedActivity</span></span>|<span data-ttu-id="03e95-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="03e95-131">xs:string</span></span>|<span data-ttu-id="03e95-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="03e95-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="03e95-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="03e95-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="03e95-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="03e95-134">xs:string</span></span>|<span data-ttu-id="03e95-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="03e95-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="03e95-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="03e95-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="03e95-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="03e95-137">xs:string</span></span>|<span data-ttu-id="03e95-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="03e95-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="03e95-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="03e95-139">AppDomain</span></span>|<span data-ttu-id="03e95-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="03e95-140">xs:string</span></span>|<span data-ttu-id="03e95-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="03e95-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

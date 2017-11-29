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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6f58cf711a91a748d3516bdd0708cc89b02c623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="75bd5-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="75bd5-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="75bd5-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="75bd5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75bd5-104">ID</span><span class="sxs-lookup"><span data-stu-id="75bd5-104">ID</span></span>|<span data-ttu-id="75bd5-105">1014</span><span class="sxs-lookup"><span data-stu-id="75bd5-105">1014</span></span>|  
|<span data-ttu-id="75bd5-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="75bd5-106">Keywords</span></span>|<span data-ttu-id="75bd5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="75bd5-107">WFRuntime</span></span>|  
|<span data-ttu-id="75bd5-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="75bd5-108">Level</span></span>|<span data-ttu-id="75bd5-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="75bd5-109">Verbose</span></span>|  
|<span data-ttu-id="75bd5-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="75bd5-110">Channel</span></span>|<span data-ttu-id="75bd5-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="75bd5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="75bd5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="75bd5-112">Description</span></span>  
 <span data-ttu-id="75bd5-113">Wskazuje, że zaplanowano element roboczy CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="75bd5-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="75bd5-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="75bd5-114">Message</span></span>  
 <span data-ttu-id="75bd5-115">Zaplanowano element roboczy CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="75bd5-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="75bd5-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="75bd5-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="75bd5-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="75bd5-117">Details</span></span>  
  
|<span data-ttu-id="75bd5-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="75bd5-118">Data Item Name</span></span>|<span data-ttu-id="75bd5-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="75bd5-119">Data Item Type</span></span>|<span data-ttu-id="75bd5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="75bd5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="75bd5-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="75bd5-121">ParentActivity</span></span>|<span data-ttu-id="75bd5-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd5-122">xs:string</span></span>|<span data-ttu-id="75bd5-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="75bd5-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="75bd5-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="75bd5-124">ParentDisplayName</span></span>|<span data-ttu-id="75bd5-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd5-125">xs:string</span></span>|<span data-ttu-id="75bd5-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="75bd5-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="75bd5-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="75bd5-127">ParentInstanceId</span></span>|<span data-ttu-id="75bd5-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd5-128">xs:string</span></span>|<span data-ttu-id="75bd5-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="75bd5-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="75bd5-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="75bd5-130">CompletedActivity</span></span>|<span data-ttu-id="75bd5-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd5-131">xs:string</span></span>|<span data-ttu-id="75bd5-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="75bd5-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="75bd5-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="75bd5-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="75bd5-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd5-134">xs:string</span></span>|<span data-ttu-id="75bd5-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="75bd5-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="75bd5-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="75bd5-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="75bd5-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd5-137">xs:string</span></span>|<span data-ttu-id="75bd5-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="75bd5-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="75bd5-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="75bd5-139">AppDomain</span></span>|<span data-ttu-id="75bd5-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="75bd5-140">xs:string</span></span>|<span data-ttu-id="75bd5-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="75bd5-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

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
ms.openlocfilehash: 3d483a681cae6328dd6111b320a12b5a064d3ff5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="2df8c-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="2df8c-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2df8c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2df8c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2df8c-104">ID</span><span class="sxs-lookup"><span data-stu-id="2df8c-104">ID</span></span>|<span data-ttu-id="2df8c-105">1014</span><span class="sxs-lookup"><span data-stu-id="2df8c-105">1014</span></span>|  
|<span data-ttu-id="2df8c-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2df8c-106">Keywords</span></span>|<span data-ttu-id="2df8c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2df8c-107">WFRuntime</span></span>|  
|<span data-ttu-id="2df8c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2df8c-108">Level</span></span>|<span data-ttu-id="2df8c-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="2df8c-109">Verbose</span></span>|  
|<span data-ttu-id="2df8c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2df8c-110">Channel</span></span>|<span data-ttu-id="2df8c-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="2df8c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2df8c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2df8c-112">Description</span></span>  
 <span data-ttu-id="2df8c-113">Wskazuje, że zaplanowano element roboczy CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="2df8c-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2df8c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2df8c-114">Message</span></span>  
 <span data-ttu-id="2df8c-115">Zaplanowano element roboczy CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2df8c-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="2df8c-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="2df8c-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2df8c-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2df8c-117">Details</span></span>  
  
|<span data-ttu-id="2df8c-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2df8c-118">Data Item Name</span></span>|<span data-ttu-id="2df8c-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2df8c-119">Data Item Type</span></span>|<span data-ttu-id="2df8c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2df8c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2df8c-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2df8c-121">ParentActivity</span></span>|<span data-ttu-id="2df8c-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="2df8c-122">xs:string</span></span>|<span data-ttu-id="2df8c-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2df8c-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="2df8c-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="2df8c-124">ParentDisplayName</span></span>|<span data-ttu-id="2df8c-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="2df8c-125">xs:string</span></span>|<span data-ttu-id="2df8c-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2df8c-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="2df8c-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="2df8c-127">ParentInstanceId</span></span>|<span data-ttu-id="2df8c-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="2df8c-128">xs:string</span></span>|<span data-ttu-id="2df8c-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2df8c-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="2df8c-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="2df8c-130">CompletedActivity</span></span>|<span data-ttu-id="2df8c-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="2df8c-131">xs:string</span></span>|<span data-ttu-id="2df8c-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="2df8c-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="2df8c-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2df8c-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="2df8c-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="2df8c-134">xs:string</span></span>|<span data-ttu-id="2df8c-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="2df8c-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="2df8c-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2df8c-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="2df8c-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="2df8c-137">xs:string</span></span>|<span data-ttu-id="2df8c-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="2df8c-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="2df8c-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="2df8c-139">AppDomain</span></span>|<span data-ttu-id="2df8c-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="2df8c-140">xs:string</span></span>|<span data-ttu-id="2df8c-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2df8c-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

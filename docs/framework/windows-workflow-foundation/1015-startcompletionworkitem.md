---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 44ef71e254a2407b416a0efc4b560bf2f6013a74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="5e43d-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="5e43d-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5e43d-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5e43d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5e43d-104">ID</span><span class="sxs-lookup"><span data-stu-id="5e43d-104">ID</span></span>|<span data-ttu-id="5e43d-105">1015</span><span class="sxs-lookup"><span data-stu-id="5e43d-105">1015</span></span>|  
|<span data-ttu-id="5e43d-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="5e43d-106">Keywords</span></span>|<span data-ttu-id="5e43d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5e43d-107">WFRuntime</span></span>|  
|<span data-ttu-id="5e43d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="5e43d-108">Level</span></span>|<span data-ttu-id="5e43d-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="5e43d-109">Verbose</span></span>|  
|<span data-ttu-id="5e43d-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="5e43d-110">Channel</span></span>|<span data-ttu-id="5e43d-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="5e43d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5e43d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5e43d-112">Description</span></span>  
 <span data-ttu-id="5e43d-113">Wskazuje, że element roboczy CompletionWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5e43d-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5e43d-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="5e43d-114">Message</span></span>  
 <span data-ttu-id="5e43d-115">Rozpoczęcie wykonywania elementu roboczego CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="5e43d-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="5e43d-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="5e43d-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5e43d-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="5e43d-117">Details</span></span>  
  
|<span data-ttu-id="5e43d-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="5e43d-118">Data Item Name</span></span>|<span data-ttu-id="5e43d-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="5e43d-119">Data Item Type</span></span>|<span data-ttu-id="5e43d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="5e43d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5e43d-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5e43d-121">ParentActivity</span></span>|<span data-ttu-id="5e43d-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="5e43d-122">xs:string</span></span>|<span data-ttu-id="5e43d-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5e43d-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="5e43d-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="5e43d-124">ParentDisplayName</span></span>|<span data-ttu-id="5e43d-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="5e43d-125">xs:string</span></span>|<span data-ttu-id="5e43d-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5e43d-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="5e43d-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="5e43d-127">ParentInstanceId</span></span>|<span data-ttu-id="5e43d-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="5e43d-128">xs:string</span></span>|<span data-ttu-id="5e43d-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5e43d-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="5e43d-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="5e43d-130">CompletedActivity</span></span>|<span data-ttu-id="5e43d-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="5e43d-131">xs:string</span></span>|<span data-ttu-id="5e43d-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="5e43d-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="5e43d-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="5e43d-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="5e43d-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="5e43d-134">xs:string</span></span>|<span data-ttu-id="5e43d-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="5e43d-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="5e43d-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="5e43d-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="5e43d-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="5e43d-137">xs:string</span></span>|<span data-ttu-id="5e43d-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="5e43d-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="5e43d-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="5e43d-139">AppDomain</span></span>|<span data-ttu-id="5e43d-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="5e43d-140">xs:string</span></span>|<span data-ttu-id="5e43d-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5e43d-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

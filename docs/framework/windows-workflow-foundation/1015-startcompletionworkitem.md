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
ms.workload: dotnet
ms.openlocfilehash: bc317157ed7658a52aa60c9b74942f9e84d47257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="42214-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="42214-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="42214-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="42214-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42214-104">ID</span><span class="sxs-lookup"><span data-stu-id="42214-104">ID</span></span>|<span data-ttu-id="42214-105">1015</span><span class="sxs-lookup"><span data-stu-id="42214-105">1015</span></span>|  
|<span data-ttu-id="42214-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="42214-106">Keywords</span></span>|<span data-ttu-id="42214-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="42214-107">WFRuntime</span></span>|  
|<span data-ttu-id="42214-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="42214-108">Level</span></span>|<span data-ttu-id="42214-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="42214-109">Verbose</span></span>|  
|<span data-ttu-id="42214-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="42214-110">Channel</span></span>|<span data-ttu-id="42214-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="42214-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="42214-112">Opis</span><span class="sxs-lookup"><span data-stu-id="42214-112">Description</span></span>  
 <span data-ttu-id="42214-113">Wskazuje, że element roboczy CompletionWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="42214-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="42214-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="42214-114">Message</span></span>  
 <span data-ttu-id="42214-115">Rozpoczęcie wykonywania elementu roboczego CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="42214-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="42214-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="42214-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="42214-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="42214-117">Details</span></span>  
  
|<span data-ttu-id="42214-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="42214-118">Data Item Name</span></span>|<span data-ttu-id="42214-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="42214-119">Data Item Type</span></span>|<span data-ttu-id="42214-120">Opis</span><span class="sxs-lookup"><span data-stu-id="42214-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="42214-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="42214-121">ParentActivity</span></span>|<span data-ttu-id="42214-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="42214-122">xs:string</span></span>|<span data-ttu-id="42214-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="42214-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="42214-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="42214-124">ParentDisplayName</span></span>|<span data-ttu-id="42214-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="42214-125">xs:string</span></span>|<span data-ttu-id="42214-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="42214-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="42214-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="42214-127">ParentInstanceId</span></span>|<span data-ttu-id="42214-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="42214-128">xs:string</span></span>|<span data-ttu-id="42214-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="42214-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="42214-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="42214-130">CompletedActivity</span></span>|<span data-ttu-id="42214-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="42214-131">xs:string</span></span>|<span data-ttu-id="42214-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="42214-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="42214-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="42214-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="42214-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="42214-134">xs:string</span></span>|<span data-ttu-id="42214-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="42214-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="42214-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="42214-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="42214-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="42214-137">xs:string</span></span>|<span data-ttu-id="42214-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="42214-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="42214-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="42214-139">AppDomain</span></span>|<span data-ttu-id="42214-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="42214-140">xs:string</span></span>|<span data-ttu-id="42214-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="42214-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

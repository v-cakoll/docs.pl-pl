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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7457b65f81e9e26b9de6055df474a83ce4264846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="d23b0-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="d23b0-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d23b0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d23b0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d23b0-104">ID</span><span class="sxs-lookup"><span data-stu-id="d23b0-104">ID</span></span>|<span data-ttu-id="d23b0-105">1015</span><span class="sxs-lookup"><span data-stu-id="d23b0-105">1015</span></span>|  
|<span data-ttu-id="d23b0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d23b0-106">Keywords</span></span>|<span data-ttu-id="d23b0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d23b0-107">WFRuntime</span></span>|  
|<span data-ttu-id="d23b0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d23b0-108">Level</span></span>|<span data-ttu-id="d23b0-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="d23b0-109">Verbose</span></span>|  
|<span data-ttu-id="d23b0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d23b0-110">Channel</span></span>|<span data-ttu-id="d23b0-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="d23b0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d23b0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d23b0-112">Description</span></span>  
 <span data-ttu-id="d23b0-113">Wskazuje, że element roboczy CompletionWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d23b0-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d23b0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d23b0-114">Message</span></span>  
 <span data-ttu-id="d23b0-115">Rozpoczęcie wykonywania elementu roboczego CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d23b0-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="d23b0-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="d23b0-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d23b0-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d23b0-117">Details</span></span>  
  
|<span data-ttu-id="d23b0-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d23b0-118">Data Item Name</span></span>|<span data-ttu-id="d23b0-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d23b0-119">Data Item Type</span></span>|<span data-ttu-id="d23b0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d23b0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d23b0-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d23b0-121">ParentActivity</span></span>|<span data-ttu-id="d23b0-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="d23b0-122">xs:string</span></span>|<span data-ttu-id="d23b0-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d23b0-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="d23b0-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="d23b0-124">ParentDisplayName</span></span>|<span data-ttu-id="d23b0-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="d23b0-125">xs:string</span></span>|<span data-ttu-id="d23b0-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d23b0-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="d23b0-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="d23b0-127">ParentInstanceId</span></span>|<span data-ttu-id="d23b0-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="d23b0-128">xs:string</span></span>|<span data-ttu-id="d23b0-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d23b0-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="d23b0-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="d23b0-130">CompletedActivity</span></span>|<span data-ttu-id="d23b0-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="d23b0-131">xs:string</span></span>|<span data-ttu-id="d23b0-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="d23b0-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="d23b0-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="d23b0-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="d23b0-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="d23b0-134">xs:string</span></span>|<span data-ttu-id="d23b0-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="d23b0-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="d23b0-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="d23b0-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="d23b0-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="d23b0-137">xs:string</span></span>|<span data-ttu-id="d23b0-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="d23b0-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="d23b0-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d23b0-139">AppDomain</span></span>|<span data-ttu-id="d23b0-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="d23b0-140">xs:string</span></span>|<span data-ttu-id="d23b0-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d23b0-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a0d8cc3d17ecd13d9312b42554ef5347cccf213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="4acef-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="4acef-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="4acef-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4acef-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4acef-104">ID</span><span class="sxs-lookup"><span data-stu-id="4acef-104">ID</span></span>|<span data-ttu-id="4acef-105">1009</span><span class="sxs-lookup"><span data-stu-id="4acef-105">1009</span></span>|  
|<span data-ttu-id="4acef-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4acef-106">Keywords</span></span>|<span data-ttu-id="4acef-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4acef-107">WFRuntime</span></span>|  
|<span data-ttu-id="4acef-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="4acef-108">Level</span></span>|<span data-ttu-id="4acef-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="4acef-109">Information</span></span>|  
|<span data-ttu-id="4acef-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="4acef-110">Channel</span></span>|<span data-ttu-id="4acef-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="4acef-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4acef-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4acef-112">Description</span></span>  
 <span data-ttu-id="4acef-113">Wskazuje, że działanie jest zaplanowane co do wykonania.</span><span class="sxs-lookup"><span data-stu-id="4acef-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4acef-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="4acef-114">Message</span></span>  
 <span data-ttu-id="4acef-115">Działanie "%1", nazwa wyświetlana nadrzędne: "%2", identyfikator wystąpienia: '%3' zaplanowało działanie podrzędne %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="4acef-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4acef-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4acef-116">Details</span></span>  
  
|<span data-ttu-id="4acef-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="4acef-117">Data Item Name</span></span>|<span data-ttu-id="4acef-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="4acef-118">Data Item Type</span></span>|<span data-ttu-id="4acef-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4acef-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4acef-120">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4acef-120">ParentActivity</span></span>|<span data-ttu-id="4acef-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="4acef-121">xs:string</span></span>|<span data-ttu-id="4acef-122">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4acef-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="4acef-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="4acef-123">ParentDisplayName</span></span>|<span data-ttu-id="4acef-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="4acef-124">xs:string</span></span>|<span data-ttu-id="4acef-125">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4acef-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="4acef-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="4acef-126">ParentInstanceId</span></span>|<span data-ttu-id="4acef-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="4acef-127">xs:string</span></span>|<span data-ttu-id="4acef-128">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4acef-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="4acef-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="4acef-129">ChildActivity</span></span>|<span data-ttu-id="4acef-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="4acef-130">xs:string</span></span>|<span data-ttu-id="4acef-131">Nazwa typu działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="4acef-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="4acef-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="4acef-132">ChildDisplayName</span></span>|<span data-ttu-id="4acef-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="4acef-133">xs:string</span></span>|<span data-ttu-id="4acef-134">Nazwa wyświetlana działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="4acef-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="4acef-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="4acef-135">ChildInstanceId</span></span>|<span data-ttu-id="4acef-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="4acef-136">xs:string</span></span>|<span data-ttu-id="4acef-137">Identyfikator wystąpienia działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="4acef-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="4acef-138">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="4acef-138">AppDomain</span></span>|<span data-ttu-id="4acef-139">xs:String</span><span class="sxs-lookup"><span data-stu-id="4acef-139">xs:string</span></span>|<span data-ttu-id="4acef-140">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4acef-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

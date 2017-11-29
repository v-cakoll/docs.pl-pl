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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9463fbf2e7f2ac3424488dc3fca322a91d11126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="7b56b-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="7b56b-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="7b56b-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7b56b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7b56b-104">ID</span><span class="sxs-lookup"><span data-stu-id="7b56b-104">ID</span></span>|<span data-ttu-id="7b56b-105">1009</span><span class="sxs-lookup"><span data-stu-id="7b56b-105">1009</span></span>|  
|<span data-ttu-id="7b56b-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7b56b-106">Keywords</span></span>|<span data-ttu-id="7b56b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7b56b-107">WFRuntime</span></span>|  
|<span data-ttu-id="7b56b-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7b56b-108">Level</span></span>|<span data-ttu-id="7b56b-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="7b56b-109">Information</span></span>|  
|<span data-ttu-id="7b56b-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7b56b-110">Channel</span></span>|<span data-ttu-id="7b56b-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="7b56b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7b56b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7b56b-112">Description</span></span>  
 <span data-ttu-id="7b56b-113">Wskazuje, że działanie jest zaplanowane co do wykonania.</span><span class="sxs-lookup"><span data-stu-id="7b56b-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7b56b-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7b56b-114">Message</span></span>  
 <span data-ttu-id="7b56b-115">Działanie "%1", nazwa wyświetlana nadrzędne: "%2", identyfikator wystąpienia: '%3' zaplanowało działanie podrzędne %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="7b56b-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7b56b-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7b56b-116">Details</span></span>  
  
|<span data-ttu-id="7b56b-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7b56b-117">Data Item Name</span></span>|<span data-ttu-id="7b56b-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7b56b-118">Data Item Type</span></span>|<span data-ttu-id="7b56b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7b56b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7b56b-120">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7b56b-120">ParentActivity</span></span>|<span data-ttu-id="7b56b-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="7b56b-121">xs:string</span></span>|<span data-ttu-id="7b56b-122">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="7b56b-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="7b56b-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="7b56b-123">ParentDisplayName</span></span>|<span data-ttu-id="7b56b-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="7b56b-124">xs:string</span></span>|<span data-ttu-id="7b56b-125">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="7b56b-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="7b56b-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="7b56b-126">ParentInstanceId</span></span>|<span data-ttu-id="7b56b-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="7b56b-127">xs:string</span></span>|<span data-ttu-id="7b56b-128">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="7b56b-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="7b56b-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="7b56b-129">ChildActivity</span></span>|<span data-ttu-id="7b56b-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="7b56b-130">xs:string</span></span>|<span data-ttu-id="7b56b-131">Nazwa typu działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="7b56b-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="7b56b-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="7b56b-132">ChildDisplayName</span></span>|<span data-ttu-id="7b56b-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="7b56b-133">xs:string</span></span>|<span data-ttu-id="7b56b-134">Nazwa wyświetlana działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="7b56b-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="7b56b-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="7b56b-135">ChildInstanceId</span></span>|<span data-ttu-id="7b56b-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="7b56b-136">xs:string</span></span>|<span data-ttu-id="7b56b-137">Identyfikator wystąpienia działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="7b56b-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="7b56b-138">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="7b56b-138">AppDomain</span></span>|<span data-ttu-id="7b56b-139">xs:String</span><span class="sxs-lookup"><span data-stu-id="7b56b-139">xs:string</span></span>|<span data-ttu-id="7b56b-140">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7b56b-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

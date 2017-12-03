---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fcd6662c0f8899b6830dc8e06cee4f56b5ff906
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="03901-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="03901-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="03901-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="03901-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03901-104">ID</span><span class="sxs-lookup"><span data-stu-id="03901-104">ID</span></span>|<span data-ttu-id="03901-105">1035</span><span class="sxs-lookup"><span data-stu-id="03901-105">1035</span></span>|  
|<span data-ttu-id="03901-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="03901-106">Keywords</span></span>|<span data-ttu-id="03901-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="03901-107">WFRuntime</span></span>|  
|<span data-ttu-id="03901-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="03901-108">Level</span></span>|<span data-ttu-id="03901-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="03901-109">Verbose</span></span>|  
|<span data-ttu-id="03901-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="03901-110">Channel</span></span>|<span data-ttu-id="03901-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="03901-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03901-112">Opis</span><span class="sxs-lookup"><span data-stu-id="03901-112">Description</span></span>  
 <span data-ttu-id="03901-113">Wskazuje, że działanie ustawił transakcja czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="03901-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03901-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="03901-114">Message</span></span>  
 <span data-ttu-id="03901-115">Transakcja czasu wykonywania została ustawiona przez działanie %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="03901-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="03901-116">Wykonanie izolowane, ograniczone do działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="03901-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03901-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="03901-117">Details</span></span>  
  
|<span data-ttu-id="03901-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="03901-118">Data Item Name</span></span>|<span data-ttu-id="03901-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="03901-119">Data Item Type</span></span>|<span data-ttu-id="03901-120">Opis</span><span class="sxs-lookup"><span data-stu-id="03901-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="03901-121">Działanie</span><span class="sxs-lookup"><span data-stu-id="03901-121">Activity</span></span>|<span data-ttu-id="03901-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="03901-122">xs:string</span></span>|<span data-ttu-id="03901-123">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="03901-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="03901-124">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="03901-124">DisplayName</span></span>|<span data-ttu-id="03901-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="03901-125">xs:string</span></span>|<span data-ttu-id="03901-126">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="03901-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="03901-127">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="03901-127">InstanceId</span></span>|<span data-ttu-id="03901-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="03901-128">xs:string</span></span>|<span data-ttu-id="03901-129">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="03901-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="03901-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="03901-130">IsolatedActivity</span></span>|<span data-ttu-id="03901-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="03901-131">xs:string</span></span>|<span data-ttu-id="03901-132">Nazwa typu transakcji jest izolowane, ograniczone do działania.</span><span class="sxs-lookup"><span data-stu-id="03901-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="03901-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="03901-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="03901-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="03901-134">xs:string</span></span>|<span data-ttu-id="03901-135">Nazwa wyświetlana transakcji jest izolowane, ograniczone do działania.</span><span class="sxs-lookup"><span data-stu-id="03901-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="03901-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="03901-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="03901-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="03901-137">xs:string</span></span>|<span data-ttu-id="03901-138">Identyfikator wystąpienia transakcji jest izolowane, ograniczone do działania.</span><span class="sxs-lookup"><span data-stu-id="03901-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="03901-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="03901-139">AppDomain</span></span>|<span data-ttu-id="03901-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="03901-140">xs:string</span></span>|<span data-ttu-id="03901-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="03901-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

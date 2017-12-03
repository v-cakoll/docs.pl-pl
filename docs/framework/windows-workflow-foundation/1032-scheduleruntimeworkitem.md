---
title: 1032 - ScheduleRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2a150b9e9c78a9ce1f5e20b962a58ef2d5dde9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="db03c-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="db03c-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="db03c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="db03c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db03c-104">ID</span><span class="sxs-lookup"><span data-stu-id="db03c-104">ID</span></span>|<span data-ttu-id="db03c-105">1032</span><span class="sxs-lookup"><span data-stu-id="db03c-105">1032</span></span>|  
|<span data-ttu-id="db03c-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="db03c-106">Keywords</span></span>|<span data-ttu-id="db03c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="db03c-107">WFRuntime</span></span>|  
|<span data-ttu-id="db03c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="db03c-108">Level</span></span>|<span data-ttu-id="db03c-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="db03c-109">Verbose</span></span>|  
|<span data-ttu-id="db03c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="db03c-110">Channel</span></span>|<span data-ttu-id="db03c-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="db03c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db03c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="db03c-112">Description</span></span>  
 <span data-ttu-id="db03c-113">Wskazuje, że zaplanowano RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="db03c-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="db03c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="db03c-114">Message</span></span>  
 <span data-ttu-id="db03c-115">Zaplanowano element roboczy środowiska wykonawczego dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="db03c-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="db03c-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="db03c-116">Details</span></span>  
  
|<span data-ttu-id="db03c-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="db03c-117">Data Item Name</span></span>|<span data-ttu-id="db03c-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="db03c-118">Data Item Type</span></span>|<span data-ttu-id="db03c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="db03c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="db03c-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="db03c-120">Activity</span></span>|<span data-ttu-id="db03c-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="db03c-121">xs:string</span></span>|<span data-ttu-id="db03c-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="db03c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="db03c-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="db03c-123">DisplayName</span></span>|<span data-ttu-id="db03c-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="db03c-124">xs:string</span></span>|<span data-ttu-id="db03c-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="db03c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="db03c-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="db03c-126">InstanceId</span></span>|<span data-ttu-id="db03c-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="db03c-127">xs:string</span></span>|<span data-ttu-id="db03c-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="db03c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="db03c-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="db03c-129">AppDomain</span></span>|<span data-ttu-id="db03c-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="db03c-130">xs:string</span></span>|<span data-ttu-id="db03c-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="db03c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

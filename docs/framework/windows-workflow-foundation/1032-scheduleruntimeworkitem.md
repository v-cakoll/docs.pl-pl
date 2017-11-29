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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4de69b1fc2647d7723db8aebb02942938db7478f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="e71fb-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="e71fb-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e71fb-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e71fb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e71fb-104">ID</span><span class="sxs-lookup"><span data-stu-id="e71fb-104">ID</span></span>|<span data-ttu-id="e71fb-105">1032</span><span class="sxs-lookup"><span data-stu-id="e71fb-105">1032</span></span>|  
|<span data-ttu-id="e71fb-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e71fb-106">Keywords</span></span>|<span data-ttu-id="e71fb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e71fb-107">WFRuntime</span></span>|  
|<span data-ttu-id="e71fb-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e71fb-108">Level</span></span>|<span data-ttu-id="e71fb-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="e71fb-109">Verbose</span></span>|  
|<span data-ttu-id="e71fb-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e71fb-110">Channel</span></span>|<span data-ttu-id="e71fb-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="e71fb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e71fb-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e71fb-112">Description</span></span>  
 <span data-ttu-id="e71fb-113">Wskazuje, że zaplanowano RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="e71fb-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e71fb-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e71fb-114">Message</span></span>  
 <span data-ttu-id="e71fb-115">Zaplanowano element roboczy środowiska wykonawczego dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e71fb-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e71fb-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e71fb-116">Details</span></span>  
  
|<span data-ttu-id="e71fb-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e71fb-117">Data Item Name</span></span>|<span data-ttu-id="e71fb-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e71fb-118">Data Item Type</span></span>|<span data-ttu-id="e71fb-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e71fb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e71fb-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="e71fb-120">Activity</span></span>|<span data-ttu-id="e71fb-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="e71fb-121">xs:string</span></span>|<span data-ttu-id="e71fb-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="e71fb-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e71fb-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="e71fb-123">DisplayName</span></span>|<span data-ttu-id="e71fb-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="e71fb-124">xs:string</span></span>|<span data-ttu-id="e71fb-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="e71fb-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e71fb-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="e71fb-126">InstanceId</span></span>|<span data-ttu-id="e71fb-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="e71fb-127">xs:string</span></span>|<span data-ttu-id="e71fb-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="e71fb-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e71fb-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e71fb-129">AppDomain</span></span>|<span data-ttu-id="e71fb-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="e71fb-130">xs:string</span></span>|<span data-ttu-id="e71fb-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e71fb-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

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
ms.workload: dotnet
ms.openlocfilehash: 81cc73a5ab58e90f1a0ee5bdaf9a491d20206fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="ae6d2-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="ae6d2-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ae6d2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ae6d2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae6d2-104">ID</span><span class="sxs-lookup"><span data-stu-id="ae6d2-104">ID</span></span>|<span data-ttu-id="ae6d2-105">1032</span><span class="sxs-lookup"><span data-stu-id="ae6d2-105">1032</span></span>|  
|<span data-ttu-id="ae6d2-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ae6d2-106">Keywords</span></span>|<span data-ttu-id="ae6d2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ae6d2-107">WFRuntime</span></span>|  
|<span data-ttu-id="ae6d2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae6d2-108">Level</span></span>|<span data-ttu-id="ae6d2-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="ae6d2-109">Verbose</span></span>|  
|<span data-ttu-id="ae6d2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ae6d2-110">Channel</span></span>|<span data-ttu-id="ae6d2-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="ae6d2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae6d2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ae6d2-112">Description</span></span>  
 <span data-ttu-id="ae6d2-113">Wskazuje, że zaplanowano RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="ae6d2-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae6d2-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ae6d2-114">Message</span></span>  
 <span data-ttu-id="ae6d2-115">Zaplanowano element roboczy środowiska wykonawczego dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ae6d2-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae6d2-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ae6d2-116">Details</span></span>  
  
|<span data-ttu-id="ae6d2-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ae6d2-117">Data Item Name</span></span>|<span data-ttu-id="ae6d2-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ae6d2-118">Data Item Type</span></span>|<span data-ttu-id="ae6d2-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ae6d2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae6d2-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="ae6d2-120">Activity</span></span>|<span data-ttu-id="ae6d2-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae6d2-121">xs:string</span></span>|<span data-ttu-id="ae6d2-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="ae6d2-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="ae6d2-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="ae6d2-123">DisplayName</span></span>|<span data-ttu-id="ae6d2-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae6d2-124">xs:string</span></span>|<span data-ttu-id="ae6d2-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="ae6d2-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="ae6d2-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="ae6d2-126">InstanceId</span></span>|<span data-ttu-id="ae6d2-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae6d2-127">xs:string</span></span>|<span data-ttu-id="ae6d2-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="ae6d2-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ae6d2-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ae6d2-129">AppDomain</span></span>|<span data-ttu-id="ae6d2-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="ae6d2-130">xs:string</span></span>|<span data-ttu-id="ae6d2-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ae6d2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

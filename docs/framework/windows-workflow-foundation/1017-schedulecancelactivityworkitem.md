---
title: 1017 - ScheduleCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b524f083c49f517c21c77da4f1d1488625a575b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="33286-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="33286-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="33286-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="33286-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33286-104">ID</span><span class="sxs-lookup"><span data-stu-id="33286-104">ID</span></span>|<span data-ttu-id="33286-105">1017</span><span class="sxs-lookup"><span data-stu-id="33286-105">1017</span></span>|  
|<span data-ttu-id="33286-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="33286-106">Keywords</span></span>|<span data-ttu-id="33286-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="33286-107">WFRuntime</span></span>|  
|<span data-ttu-id="33286-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="33286-108">Level</span></span>|<span data-ttu-id="33286-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="33286-109">Verbose</span></span>|  
|<span data-ttu-id="33286-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="33286-110">Channel</span></span>|<span data-ttu-id="33286-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="33286-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="33286-112">Opis</span><span class="sxs-lookup"><span data-stu-id="33286-112">Description</span></span>  
 <span data-ttu-id="33286-113">Wskazuje, że zaplanowano element roboczy CancelActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="33286-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="33286-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="33286-114">Message</span></span>  
 <span data-ttu-id="33286-115">Zaplanowano element roboczy CancelActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="33286-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="33286-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="33286-116">Details</span></span>  
  
|<span data-ttu-id="33286-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="33286-117">Data Item Name</span></span>|<span data-ttu-id="33286-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="33286-118">Data Item Type</span></span>|<span data-ttu-id="33286-119">Opis</span><span class="sxs-lookup"><span data-stu-id="33286-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="33286-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="33286-120">Activity</span></span>|<span data-ttu-id="33286-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="33286-121">xs:string</span></span>|<span data-ttu-id="33286-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="33286-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="33286-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="33286-123">DisplayName</span></span>|<span data-ttu-id="33286-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="33286-124">xs:string</span></span>|<span data-ttu-id="33286-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="33286-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="33286-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="33286-126">InstanceId</span></span>|<span data-ttu-id="33286-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="33286-127">xs:string</span></span>|<span data-ttu-id="33286-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="33286-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="33286-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="33286-129">AppDomain</span></span>|<span data-ttu-id="33286-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="33286-130">xs:string</span></span>|<span data-ttu-id="33286-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="33286-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

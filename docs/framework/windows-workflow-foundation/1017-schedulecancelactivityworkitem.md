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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6d348ec18b4d5eff7156d1e9809eb793ac1681d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="65478-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="65478-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="65478-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="65478-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65478-104">ID</span><span class="sxs-lookup"><span data-stu-id="65478-104">ID</span></span>|<span data-ttu-id="65478-105">1017</span><span class="sxs-lookup"><span data-stu-id="65478-105">1017</span></span>|  
|<span data-ttu-id="65478-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="65478-106">Keywords</span></span>|<span data-ttu-id="65478-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="65478-107">WFRuntime</span></span>|  
|<span data-ttu-id="65478-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="65478-108">Level</span></span>|<span data-ttu-id="65478-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="65478-109">Verbose</span></span>|  
|<span data-ttu-id="65478-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="65478-110">Channel</span></span>|<span data-ttu-id="65478-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="65478-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="65478-112">Opis</span><span class="sxs-lookup"><span data-stu-id="65478-112">Description</span></span>  
 <span data-ttu-id="65478-113">Wskazuje, że zaplanowano element roboczy CancelActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="65478-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="65478-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="65478-114">Message</span></span>  
 <span data-ttu-id="65478-115">Zaplanowano element roboczy CancelActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="65478-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="65478-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="65478-116">Details</span></span>  
  
|<span data-ttu-id="65478-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="65478-117">Data Item Name</span></span>|<span data-ttu-id="65478-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="65478-118">Data Item Type</span></span>|<span data-ttu-id="65478-119">Opis</span><span class="sxs-lookup"><span data-stu-id="65478-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="65478-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="65478-120">Activity</span></span>|<span data-ttu-id="65478-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="65478-121">xs:string</span></span>|<span data-ttu-id="65478-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="65478-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="65478-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="65478-123">DisplayName</span></span>|<span data-ttu-id="65478-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="65478-124">xs:string</span></span>|<span data-ttu-id="65478-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="65478-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="65478-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="65478-126">InstanceId</span></span>|<span data-ttu-id="65478-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="65478-127">xs:string</span></span>|<span data-ttu-id="65478-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="65478-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="65478-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="65478-129">AppDomain</span></span>|<span data-ttu-id="65478-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="65478-130">xs:string</span></span>|<span data-ttu-id="65478-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="65478-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

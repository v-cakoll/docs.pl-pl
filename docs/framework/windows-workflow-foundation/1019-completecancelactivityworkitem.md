---
title: 1019 - CompleteCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f8af4486d4659afd4c98016a6f88719271f1a1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="47535-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="47535-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="47535-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="47535-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47535-104">ID</span><span class="sxs-lookup"><span data-stu-id="47535-104">ID</span></span>|<span data-ttu-id="47535-105">1019</span><span class="sxs-lookup"><span data-stu-id="47535-105">1019</span></span>|  
|<span data-ttu-id="47535-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="47535-106">Keywords</span></span>|<span data-ttu-id="47535-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="47535-107">WFRuntime</span></span>|  
|<span data-ttu-id="47535-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="47535-108">Level</span></span>|<span data-ttu-id="47535-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="47535-109">Verbose</span></span>|  
|<span data-ttu-id="47535-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="47535-110">Channel</span></span>|<span data-ttu-id="47535-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="47535-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="47535-112">Opis</span><span class="sxs-lookup"><span data-stu-id="47535-112">Description</span></span>  
 <span data-ttu-id="47535-113">Wskazuje, że element roboczy CancelActivityWorkItem została ukończona.</span><span class="sxs-lookup"><span data-stu-id="47535-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="47535-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="47535-114">Message</span></span>  
 <span data-ttu-id="47535-115">Ukończono element roboczy CancelActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="47535-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="47535-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="47535-116">Details</span></span>  
  
|<span data-ttu-id="47535-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="47535-117">Data Item Name</span></span>|<span data-ttu-id="47535-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="47535-118">Data Item Type</span></span>|<span data-ttu-id="47535-119">Opis</span><span class="sxs-lookup"><span data-stu-id="47535-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="47535-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="47535-120">Activity</span></span>|<span data-ttu-id="47535-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="47535-121">xs:string</span></span>|<span data-ttu-id="47535-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="47535-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="47535-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="47535-123">DisplayName</span></span>|<span data-ttu-id="47535-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="47535-124">xs:string</span></span>|<span data-ttu-id="47535-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="47535-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="47535-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="47535-126">InstanceId</span></span>|<span data-ttu-id="47535-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="47535-127">xs:string</span></span>|<span data-ttu-id="47535-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="47535-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="47535-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="47535-129">AppDomain</span></span>|<span data-ttu-id="47535-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="47535-130">xs:string</span></span>|<span data-ttu-id="47535-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="47535-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1012 - StartExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a3b03e8ac24bc1652b88b71e8c25862a07c194f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="76735-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="76735-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="76735-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="76735-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76735-104">ID</span><span class="sxs-lookup"><span data-stu-id="76735-104">ID</span></span>|<span data-ttu-id="76735-105">1012</span><span class="sxs-lookup"><span data-stu-id="76735-105">1012</span></span>|  
|<span data-ttu-id="76735-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="76735-106">Keywords</span></span>|<span data-ttu-id="76735-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="76735-107">WFRuntime</span></span>|  
|<span data-ttu-id="76735-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="76735-108">Level</span></span>|<span data-ttu-id="76735-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="76735-109">Verbose</span></span>|  
|<span data-ttu-id="76735-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="76735-110">Channel</span></span>|<span data-ttu-id="76735-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="76735-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="76735-112">Opis</span><span class="sxs-lookup"><span data-stu-id="76735-112">Description</span></span>  
 <span data-ttu-id="76735-113">Wskazuje, że element roboczy ExecuteActivityWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="76735-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="76735-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="76735-114">Message</span></span>  
 <span data-ttu-id="76735-115">Rozpoczęcie wykonywania elementu roboczego ExecuteActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="76735-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="76735-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="76735-116">Details</span></span>  
  
|<span data-ttu-id="76735-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="76735-117">Data Item Name</span></span>|<span data-ttu-id="76735-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="76735-118">Data Item Type</span></span>|<span data-ttu-id="76735-119">Opis</span><span class="sxs-lookup"><span data-stu-id="76735-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="76735-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="76735-120">Activity</span></span>|<span data-ttu-id="76735-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="76735-121">xs:string</span></span>|<span data-ttu-id="76735-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="76735-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="76735-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="76735-123">DisplayName</span></span>|<span data-ttu-id="76735-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="76735-124">xs:string</span></span>|<span data-ttu-id="76735-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="76735-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="76735-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="76735-126">InstanceId</span></span>|<span data-ttu-id="76735-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="76735-127">xs:string</span></span>|<span data-ttu-id="76735-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="76735-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="76735-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="76735-129">AppDomain</span></span>|<span data-ttu-id="76735-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="76735-130">xs:string</span></span>|<span data-ttu-id="76735-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="76735-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

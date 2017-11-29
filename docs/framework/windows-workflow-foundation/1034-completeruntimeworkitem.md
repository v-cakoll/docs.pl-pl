---
title: 1034 - CompleteRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63ab145b8a0688a7f7bbf7dbcbe8dfe612eab294
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="16fe4-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="16fe4-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="16fe4-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="16fe4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16fe4-104">ID</span><span class="sxs-lookup"><span data-stu-id="16fe4-104">ID</span></span>|<span data-ttu-id="16fe4-105">1034</span><span class="sxs-lookup"><span data-stu-id="16fe4-105">1034</span></span>|  
|<span data-ttu-id="16fe4-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="16fe4-106">Keywords</span></span>|<span data-ttu-id="16fe4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="16fe4-107">WFRuntime</span></span>|  
|<span data-ttu-id="16fe4-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="16fe4-108">Level</span></span>|<span data-ttu-id="16fe4-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="16fe4-109">Verbose</span></span>|  
|<span data-ttu-id="16fe4-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="16fe4-110">Channel</span></span>|<span data-ttu-id="16fe4-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="16fe4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16fe4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="16fe4-112">Description</span></span>  
 <span data-ttu-id="16fe4-113">Wskazuje, że RuntimeWorkItem została ukończona.</span><span class="sxs-lookup"><span data-stu-id="16fe4-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="16fe4-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="16fe4-114">Message</span></span>  
 <span data-ttu-id="16fe4-115">Ukończono element roboczy środowiska wykonawczego dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="16fe4-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16fe4-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="16fe4-116">Details</span></span>  
  
|<span data-ttu-id="16fe4-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="16fe4-117">Data Item Name</span></span>|<span data-ttu-id="16fe4-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="16fe4-118">Data Item Type</span></span>|<span data-ttu-id="16fe4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="16fe4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16fe4-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="16fe4-120">Activity</span></span>|<span data-ttu-id="16fe4-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="16fe4-121">xs:string</span></span>|<span data-ttu-id="16fe4-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="16fe4-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="16fe4-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="16fe4-123">DisplayName</span></span>|<span data-ttu-id="16fe4-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="16fe4-124">xs:string</span></span>|<span data-ttu-id="16fe4-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="16fe4-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="16fe4-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="16fe4-126">InstanceId</span></span>|<span data-ttu-id="16fe4-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="16fe4-127">xs:string</span></span>|<span data-ttu-id="16fe4-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="16fe4-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="16fe4-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="16fe4-129">AppDomain</span></span>|<span data-ttu-id="16fe4-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="16fe4-130">xs:string</span></span>|<span data-ttu-id="16fe4-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="16fe4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

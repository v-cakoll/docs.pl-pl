---
title: 1033 - StartRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0de8e45a592cae49060f976b28a7a7bcf8781265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="6bbea-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="6bbea-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6bbea-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6bbea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6bbea-104">ID</span><span class="sxs-lookup"><span data-stu-id="6bbea-104">ID</span></span>|<span data-ttu-id="6bbea-105">1033</span><span class="sxs-lookup"><span data-stu-id="6bbea-105">1033</span></span>|  
|<span data-ttu-id="6bbea-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6bbea-106">Keywords</span></span>|<span data-ttu-id="6bbea-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6bbea-107">WFRuntime</span></span>|  
|<span data-ttu-id="6bbea-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="6bbea-108">Level</span></span>|<span data-ttu-id="6bbea-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="6bbea-109">Verbose</span></span>|  
|<span data-ttu-id="6bbea-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="6bbea-110">Channel</span></span>|<span data-ttu-id="6bbea-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="6bbea-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6bbea-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6bbea-112">Description</span></span>  
 <span data-ttu-id="6bbea-113">Wskazuje, że RuntimeWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6bbea-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6bbea-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="6bbea-114">Message</span></span>  
 <span data-ttu-id="6bbea-115">Rozpoczęcie wykonywania elementu roboczego środowiska wykonawczego dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="6bbea-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6bbea-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6bbea-116">Details</span></span>  
  
|<span data-ttu-id="6bbea-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="6bbea-117">Data Item Name</span></span>|<span data-ttu-id="6bbea-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="6bbea-118">Data Item Type</span></span>|<span data-ttu-id="6bbea-119">Opis</span><span class="sxs-lookup"><span data-stu-id="6bbea-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6bbea-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="6bbea-120">Activity</span></span>|<span data-ttu-id="6bbea-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="6bbea-121">xs:string</span></span>|<span data-ttu-id="6bbea-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="6bbea-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="6bbea-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="6bbea-123">DisplayName</span></span>|<span data-ttu-id="6bbea-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="6bbea-124">xs:string</span></span>|<span data-ttu-id="6bbea-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="6bbea-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="6bbea-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="6bbea-126">InstanceId</span></span>|<span data-ttu-id="6bbea-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="6bbea-127">xs:string</span></span>|<span data-ttu-id="6bbea-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="6bbea-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6bbea-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="6bbea-129">AppDomain</span></span>|<span data-ttu-id="6bbea-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="6bbea-130">xs:string</span></span>|<span data-ttu-id="6bbea-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6bbea-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc60af91088fd61910dc0301b93844f4771177af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="74247-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="74247-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="74247-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="74247-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74247-104">ID</span><span class="sxs-lookup"><span data-stu-id="74247-104">ID</span></span>|<span data-ttu-id="74247-105">1012</span><span class="sxs-lookup"><span data-stu-id="74247-105">1012</span></span>|  
|<span data-ttu-id="74247-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="74247-106">Keywords</span></span>|<span data-ttu-id="74247-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="74247-107">WFRuntime</span></span>|  
|<span data-ttu-id="74247-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="74247-108">Level</span></span>|<span data-ttu-id="74247-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="74247-109">Verbose</span></span>|  
|<span data-ttu-id="74247-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="74247-110">Channel</span></span>|<span data-ttu-id="74247-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="74247-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="74247-112">Opis</span><span class="sxs-lookup"><span data-stu-id="74247-112">Description</span></span>  
 <span data-ttu-id="74247-113">Wskazuje, że element roboczy ExecuteActivityWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="74247-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="74247-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="74247-114">Message</span></span>  
 <span data-ttu-id="74247-115">Rozpoczęcie wykonywania elementu roboczego ExecuteActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="74247-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="74247-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="74247-116">Details</span></span>  
  
|<span data-ttu-id="74247-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="74247-117">Data Item Name</span></span>|<span data-ttu-id="74247-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="74247-118">Data Item Type</span></span>|<span data-ttu-id="74247-119">Opis</span><span class="sxs-lookup"><span data-stu-id="74247-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="74247-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="74247-120">Activity</span></span>|<span data-ttu-id="74247-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="74247-121">xs:string</span></span>|<span data-ttu-id="74247-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="74247-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="74247-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="74247-123">DisplayName</span></span>|<span data-ttu-id="74247-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="74247-124">xs:string</span></span>|<span data-ttu-id="74247-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="74247-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="74247-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="74247-126">InstanceId</span></span>|<span data-ttu-id="74247-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="74247-127">xs:string</span></span>|<span data-ttu-id="74247-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="74247-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="74247-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="74247-129">AppDomain</span></span>|<span data-ttu-id="74247-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="74247-130">xs:string</span></span>|<span data-ttu-id="74247-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="74247-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

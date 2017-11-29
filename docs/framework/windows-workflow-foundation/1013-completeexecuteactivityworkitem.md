---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f430e7b58d5aba277b0a35a20f1f5fdb707bce9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="de200-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="de200-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="de200-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="de200-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de200-104">ID</span><span class="sxs-lookup"><span data-stu-id="de200-104">ID</span></span>|<span data-ttu-id="de200-105">1013</span><span class="sxs-lookup"><span data-stu-id="de200-105">1013</span></span>|  
|<span data-ttu-id="de200-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="de200-106">Keywords</span></span>|<span data-ttu-id="de200-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="de200-107">WFRuntime</span></span>|  
|<span data-ttu-id="de200-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="de200-108">Level</span></span>|<span data-ttu-id="de200-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="de200-109">Verbose</span></span>|  
|<span data-ttu-id="de200-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="de200-110">Channel</span></span>|<span data-ttu-id="de200-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="de200-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="de200-112">Opis</span><span class="sxs-lookup"><span data-stu-id="de200-112">Description</span></span>  
 <span data-ttu-id="de200-113">Wskazuje, że Ukończono element roboczy ExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="de200-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="de200-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="de200-114">Message</span></span>  
 <span data-ttu-id="de200-115">Ukończono element roboczy ExecuteActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="de200-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="de200-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="de200-116">Details</span></span>  
  
|<span data-ttu-id="de200-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="de200-117">Data Item Name</span></span>|<span data-ttu-id="de200-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="de200-118">Data Item Type</span></span>|<span data-ttu-id="de200-119">Opis</span><span class="sxs-lookup"><span data-stu-id="de200-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="de200-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="de200-120">Activity</span></span>|<span data-ttu-id="de200-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="de200-121">xs:string</span></span>|<span data-ttu-id="de200-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="de200-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="de200-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="de200-123">DisplayName</span></span>|<span data-ttu-id="de200-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="de200-124">xs:string</span></span>|<span data-ttu-id="de200-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="de200-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="de200-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="de200-126">InstanceId</span></span>|<span data-ttu-id="de200-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="de200-127">xs:string</span></span>|<span data-ttu-id="de200-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="de200-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="de200-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="de200-129">AppDomain</span></span>|<span data-ttu-id="de200-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="de200-130">xs:string</span></span>|<span data-ttu-id="de200-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="de200-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

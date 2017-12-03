---
title: "1036 — RuntimeTransactionCompletionRequested"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 112063d5cd550f438541b2d775eaa49124d9cc02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="55174-102">1036 — RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="55174-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="55174-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="55174-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55174-104">ID</span><span class="sxs-lookup"><span data-stu-id="55174-104">ID</span></span>|<span data-ttu-id="55174-105">1036</span><span class="sxs-lookup"><span data-stu-id="55174-105">1036</span></span>|  
|<span data-ttu-id="55174-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="55174-106">Keywords</span></span>|<span data-ttu-id="55174-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="55174-107">WFRuntime</span></span>|  
|<span data-ttu-id="55174-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="55174-108">Level</span></span>|<span data-ttu-id="55174-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="55174-109">Verbose</span></span>|  
|<span data-ttu-id="55174-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="55174-110">Channel</span></span>|<span data-ttu-id="55174-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="55174-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="55174-112">Opis</span><span class="sxs-lookup"><span data-stu-id="55174-112">Description</span></span>  
 <span data-ttu-id="55174-113">Wskazuje, że działanie zaplanowało wykonanie transakcji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="55174-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="55174-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="55174-114">Message</span></span>  
 <span data-ttu-id="55174-115">Działanie "%1", nazwa wyświetlana: %2, identyfikator wystąpienia: '%3', zaplanowało wykonanie transakcji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="55174-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="55174-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="55174-116">Details</span></span>  
  
|<span data-ttu-id="55174-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="55174-117">Data Item Name</span></span>|<span data-ttu-id="55174-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="55174-118">Data Item Type</span></span>|<span data-ttu-id="55174-119">Opis</span><span class="sxs-lookup"><span data-stu-id="55174-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="55174-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="55174-120">Activity</span></span>|<span data-ttu-id="55174-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="55174-121">xs:string</span></span>|<span data-ttu-id="55174-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="55174-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="55174-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="55174-123">DisplayName</span></span>|<span data-ttu-id="55174-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="55174-124">xs:string</span></span>|<span data-ttu-id="55174-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="55174-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="55174-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="55174-126">InstanceId</span></span>|<span data-ttu-id="55174-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="55174-127">xs:string</span></span>|<span data-ttu-id="55174-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="55174-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="55174-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="55174-129">AppDomain</span></span>|<span data-ttu-id="55174-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="55174-130">xs:string</span></span>|<span data-ttu-id="55174-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="55174-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

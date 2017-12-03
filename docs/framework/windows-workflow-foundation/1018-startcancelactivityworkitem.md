---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b64ea860e9881ed31aa0d8e78dec55f329cc6fad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="58060-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="58060-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="58060-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="58060-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58060-104">ID</span><span class="sxs-lookup"><span data-stu-id="58060-104">ID</span></span>|<span data-ttu-id="58060-105">1018</span><span class="sxs-lookup"><span data-stu-id="58060-105">1018</span></span>|  
|<span data-ttu-id="58060-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="58060-106">Keywords</span></span>|<span data-ttu-id="58060-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="58060-107">WFRuntime</span></span>|  
|<span data-ttu-id="58060-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="58060-108">Level</span></span>|<span data-ttu-id="58060-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="58060-109">Verbose</span></span>|  
|<span data-ttu-id="58060-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="58060-110">Channel</span></span>|<span data-ttu-id="58060-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="58060-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="58060-112">Opis</span><span class="sxs-lookup"><span data-stu-id="58060-112">Description</span></span>  
 <span data-ttu-id="58060-113">Wskazuje, że element roboczy CancelActivityWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="58060-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="58060-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="58060-114">Message</span></span>  
 <span data-ttu-id="58060-115">Rozpoczęcie wykonywania elementu roboczego CancelActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="58060-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="58060-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="58060-116">Details</span></span>  
  
|<span data-ttu-id="58060-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="58060-117">Data Item Name</span></span>|<span data-ttu-id="58060-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="58060-118">Data Item Type</span></span>|<span data-ttu-id="58060-119">Opis</span><span class="sxs-lookup"><span data-stu-id="58060-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="58060-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="58060-120">Activity</span></span>|<span data-ttu-id="58060-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="58060-121">xs:string</span></span>|<span data-ttu-id="58060-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="58060-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="58060-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="58060-123">DisplayName</span></span>|<span data-ttu-id="58060-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="58060-124">xs:string</span></span>|<span data-ttu-id="58060-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="58060-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="58060-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="58060-126">InstanceId</span></span>|<span data-ttu-id="58060-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="58060-127">xs:string</span></span>|<span data-ttu-id="58060-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="58060-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="58060-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="58060-129">AppDomain</span></span>|<span data-ttu-id="58060-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="58060-130">xs:string</span></span>|<span data-ttu-id="58060-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="58060-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

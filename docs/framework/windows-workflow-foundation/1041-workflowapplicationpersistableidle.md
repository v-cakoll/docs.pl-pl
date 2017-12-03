---
title: 1041 - WorkflowApplicationPersistableIdle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b321f8c20fbd79b5e748601ee06f975dc75a7d56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="291d9-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="291d9-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="291d9-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="291d9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="291d9-104">ID</span><span class="sxs-lookup"><span data-stu-id="291d9-104">ID</span></span>|<span data-ttu-id="291d9-105">1041</span><span class="sxs-lookup"><span data-stu-id="291d9-105">1041</span></span>|  
|<span data-ttu-id="291d9-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="291d9-106">Keywords</span></span>|<span data-ttu-id="291d9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="291d9-107">WFRuntime</span></span>|  
|<span data-ttu-id="291d9-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="291d9-108">Level</span></span>|<span data-ttu-id="291d9-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="291d9-109">Information</span></span>|  
|<span data-ttu-id="291d9-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="291d9-110">Channel</span></span>|<span data-ttu-id="291d9-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="291d9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="291d9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="291d9-112">Description</span></span>  
 <span data-ttu-id="291d9-113">Wskazuje, że aplikacja przepływu pracy jest bezczynny i możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="291d9-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="291d9-114">Aplikacja przepływu pracy będą idled lub utrwalone.</span><span class="sxs-lookup"><span data-stu-id="291d9-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="291d9-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="291d9-115">Message</span></span>  
 <span data-ttu-id="291d9-116">Obiekt WorkflowApplication o identyfikatorze: "%1" jest bezczynny i możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="291d9-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="291d9-117">Zostanie podjęta następująca Akcja: %2.</span><span class="sxs-lookup"><span data-stu-id="291d9-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="291d9-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="291d9-118">Details</span></span>  
  
|<span data-ttu-id="291d9-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="291d9-119">Data Item Name</span></span>|<span data-ttu-id="291d9-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="291d9-120">Data Item Type</span></span>|<span data-ttu-id="291d9-121">Opis</span><span class="sxs-lookup"><span data-stu-id="291d9-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="291d9-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="291d9-122">WorkflowApplicationId</span></span>|<span data-ttu-id="291d9-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="291d9-123">xs:string</span></span>|<span data-ttu-id="291d9-124">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="291d9-124">The workflow application id</span></span>|  
|<span data-ttu-id="291d9-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="291d9-125">ActionTaken</span></span>|<span data-ttu-id="291d9-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="291d9-126">xs:string</span></span>|<span data-ttu-id="291d9-127">Akcja, która wpłynie na aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="291d9-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="291d9-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="291d9-128">AppDomain</span></span>|<span data-ttu-id="291d9-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="291d9-129">xs:string</span></span>|<span data-ttu-id="291d9-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="291d9-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

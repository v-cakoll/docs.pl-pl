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
ms.workload: dotnet
ms.openlocfilehash: 1efc32ed0304d5b0d222054e5c65abe279ef93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="fa784-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="fa784-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="fa784-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fa784-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa784-104">ID</span><span class="sxs-lookup"><span data-stu-id="fa784-104">ID</span></span>|<span data-ttu-id="fa784-105">1041</span><span class="sxs-lookup"><span data-stu-id="fa784-105">1041</span></span>|  
|<span data-ttu-id="fa784-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="fa784-106">Keywords</span></span>|<span data-ttu-id="fa784-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fa784-107">WFRuntime</span></span>|  
|<span data-ttu-id="fa784-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="fa784-108">Level</span></span>|<span data-ttu-id="fa784-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="fa784-109">Information</span></span>|  
|<span data-ttu-id="fa784-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="fa784-110">Channel</span></span>|<span data-ttu-id="fa784-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="fa784-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fa784-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fa784-112">Description</span></span>  
 <span data-ttu-id="fa784-113">Wskazuje, że aplikacja przepływu pracy jest bezczynny i możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="fa784-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="fa784-114">Aplikacja przepływu pracy będą idled lub utrwalone.</span><span class="sxs-lookup"><span data-stu-id="fa784-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fa784-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="fa784-115">Message</span></span>  
 <span data-ttu-id="fa784-116">Obiekt WorkflowApplication o identyfikatorze: "%1" jest bezczynny i możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="fa784-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="fa784-117">Zostanie podjęta następująca Akcja: %2.</span><span class="sxs-lookup"><span data-stu-id="fa784-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fa784-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="fa784-118">Details</span></span>  
  
|<span data-ttu-id="fa784-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="fa784-119">Data Item Name</span></span>|<span data-ttu-id="fa784-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="fa784-120">Data Item Type</span></span>|<span data-ttu-id="fa784-121">Opis</span><span class="sxs-lookup"><span data-stu-id="fa784-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fa784-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="fa784-122">WorkflowApplicationId</span></span>|<span data-ttu-id="fa784-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="fa784-123">xs:string</span></span>|<span data-ttu-id="fa784-124">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fa784-124">The workflow application id</span></span>|  
|<span data-ttu-id="fa784-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="fa784-125">ActionTaken</span></span>|<span data-ttu-id="fa784-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="fa784-126">xs:string</span></span>|<span data-ttu-id="fa784-127">Akcja, która wpłynie na aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fa784-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="fa784-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="fa784-128">AppDomain</span></span>|<span data-ttu-id="fa784-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="fa784-129">xs:string</span></span>|<span data-ttu-id="fa784-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fa784-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

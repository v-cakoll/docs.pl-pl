---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 564e94d94dc5e3579dc4a80d734db78e90db91fb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="2f2da-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="2f2da-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="2f2da-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2f2da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f2da-104">ID</span><span class="sxs-lookup"><span data-stu-id="2f2da-104">ID</span></span>|<span data-ttu-id="2f2da-105">1004</span><span class="sxs-lookup"><span data-stu-id="2f2da-105">1004</span></span>|  
|<span data-ttu-id="2f2da-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2f2da-106">Keywords</span></span>|<span data-ttu-id="2f2da-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2f2da-107">WFRuntime</span></span>|  
|<span data-ttu-id="2f2da-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2f2da-108">Level</span></span>|<span data-ttu-id="2f2da-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="2f2da-109">Information</span></span>|  
|<span data-ttu-id="2f2da-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2f2da-110">Channel</span></span>|<span data-ttu-id="2f2da-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="2f2da-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2f2da-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2f2da-112">Description</span></span>  
 <span data-ttu-id="2f2da-113">Wskazuje, że wystąpienie worfklow została przerwana z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2f2da-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2f2da-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2f2da-114">Message</span></span>  
 <span data-ttu-id="2f2da-115">Obiekt WorkflowInstance o identyfikatorze: "%1" zostało przerwane z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2f2da-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2f2da-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2f2da-116">Details</span></span>  
  
|<span data-ttu-id="2f2da-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2f2da-117">Data Item Name</span></span>|<span data-ttu-id="2f2da-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2f2da-118">Data Item Type</span></span>|<span data-ttu-id="2f2da-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2f2da-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2f2da-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2f2da-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2f2da-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2f2da-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="2f2da-122">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="2f2da-122">Exception</span></span>|`xs:string`|<span data-ttu-id="2f2da-123">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="2f2da-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="2f2da-124">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="2f2da-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2f2da-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2f2da-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7394ebbcb14850af89d906b0b573c4f677346825
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="906ec-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="906ec-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="906ec-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="906ec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="906ec-104">ID</span><span class="sxs-lookup"><span data-stu-id="906ec-104">ID</span></span>|<span data-ttu-id="906ec-105">1004</span><span class="sxs-lookup"><span data-stu-id="906ec-105">1004</span></span>|  
|<span data-ttu-id="906ec-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="906ec-106">Keywords</span></span>|<span data-ttu-id="906ec-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="906ec-107">WFRuntime</span></span>|  
|<span data-ttu-id="906ec-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="906ec-108">Level</span></span>|<span data-ttu-id="906ec-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="906ec-109">Information</span></span>|  
|<span data-ttu-id="906ec-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="906ec-110">Channel</span></span>|<span data-ttu-id="906ec-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="906ec-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="906ec-112">Opis</span><span class="sxs-lookup"><span data-stu-id="906ec-112">Description</span></span>  
 <span data-ttu-id="906ec-113">Wskazuje, że wystąpienie worfklow została przerwana z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="906ec-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="906ec-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="906ec-114">Message</span></span>  
 <span data-ttu-id="906ec-115">Obiekt WorkflowInstance o identyfikatorze: "%1" zostało przerwane z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="906ec-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="906ec-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="906ec-116">Details</span></span>  
  
|<span data-ttu-id="906ec-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="906ec-117">Data Item Name</span></span>|<span data-ttu-id="906ec-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="906ec-118">Data Item Type</span></span>|<span data-ttu-id="906ec-119">Opis</span><span class="sxs-lookup"><span data-stu-id="906ec-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="906ec-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="906ec-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="906ec-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="906ec-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="906ec-122">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="906ec-122">Exception</span></span>|`xs:string`|<span data-ttu-id="906ec-123">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="906ec-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="906ec-124">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="906ec-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="906ec-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="906ec-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

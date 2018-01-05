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
ms.workload: dotnet
ms.openlocfilehash: cc940e1781f821f12efb42c5198e77eb0451a164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="cfa58-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="cfa58-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="cfa58-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cfa58-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cfa58-104">ID</span><span class="sxs-lookup"><span data-stu-id="cfa58-104">ID</span></span>|<span data-ttu-id="cfa58-105">1004</span><span class="sxs-lookup"><span data-stu-id="cfa58-105">1004</span></span>|  
|<span data-ttu-id="cfa58-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cfa58-106">Keywords</span></span>|<span data-ttu-id="cfa58-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cfa58-107">WFRuntime</span></span>|  
|<span data-ttu-id="cfa58-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="cfa58-108">Level</span></span>|<span data-ttu-id="cfa58-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="cfa58-109">Information</span></span>|  
|<span data-ttu-id="cfa58-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="cfa58-110">Channel</span></span>|<span data-ttu-id="cfa58-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="cfa58-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cfa58-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cfa58-112">Description</span></span>  
 <span data-ttu-id="cfa58-113">Wskazuje, że wystąpienie worfklow została przerwana z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cfa58-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cfa58-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="cfa58-114">Message</span></span>  
 <span data-ttu-id="cfa58-115">Obiekt WorkflowInstance o identyfikatorze: "%1" zostało przerwane z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cfa58-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cfa58-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cfa58-116">Details</span></span>  
  
|<span data-ttu-id="cfa58-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="cfa58-117">Data Item Name</span></span>|<span data-ttu-id="cfa58-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="cfa58-118">Data Item Type</span></span>|<span data-ttu-id="cfa58-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cfa58-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cfa58-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="cfa58-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="cfa58-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="cfa58-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="cfa58-122">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="cfa58-122">Exception</span></span>|`xs:string`|<span data-ttu-id="cfa58-123">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="cfa58-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="cfa58-124">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="cfa58-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cfa58-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cfa58-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

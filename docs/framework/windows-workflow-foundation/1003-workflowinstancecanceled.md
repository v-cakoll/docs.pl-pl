---
title: 1003 - WorkflowInstanceCanceled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b264450703090edfcf99f9584c16d33eb82a76e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="01a64-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="01a64-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="01a64-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="01a64-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01a64-104">ID</span><span class="sxs-lookup"><span data-stu-id="01a64-104">ID</span></span>|<span data-ttu-id="01a64-105">1003</span><span class="sxs-lookup"><span data-stu-id="01a64-105">1003</span></span>|  
|<span data-ttu-id="01a64-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="01a64-106">Keywords</span></span>|<span data-ttu-id="01a64-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="01a64-107">WFRuntime</span></span>|  
|<span data-ttu-id="01a64-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="01a64-108">Level</span></span>|<span data-ttu-id="01a64-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="01a64-109">Information</span></span>|  
|<span data-ttu-id="01a64-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="01a64-110">Channel</span></span>|<span data-ttu-id="01a64-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="01a64-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01a64-112">Opis</span><span class="sxs-lookup"><span data-stu-id="01a64-112">Description</span></span>  
 <span data-ttu-id="01a64-113">Wskazuje, że wystąpienie przepływu pracy zostało zakończone; stan anulowane.</span><span class="sxs-lookup"><span data-stu-id="01a64-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01a64-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="01a64-114">Message</span></span>  
 <span data-ttu-id="01a64-115">Obiekt WorkflowInstance o identyfikatorze: "%1" została ukończona w stan anulowane.</span><span class="sxs-lookup"><span data-stu-id="01a64-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01a64-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="01a64-116">Details</span></span>  
  
|<span data-ttu-id="01a64-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="01a64-117">Data Item Name</span></span>|<span data-ttu-id="01a64-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="01a64-118">Data Item Type</span></span>|<span data-ttu-id="01a64-119">Opis</span><span class="sxs-lookup"><span data-stu-id="01a64-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01a64-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="01a64-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="01a64-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="01a64-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="01a64-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="01a64-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="01a64-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="01a64-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

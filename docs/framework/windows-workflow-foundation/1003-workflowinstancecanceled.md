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
ms.openlocfilehash: 6930aeed8c3cd224d5d37dcecf357195e78390ed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="54580-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="54580-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="54580-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="54580-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54580-104">ID</span><span class="sxs-lookup"><span data-stu-id="54580-104">ID</span></span>|<span data-ttu-id="54580-105">1003</span><span class="sxs-lookup"><span data-stu-id="54580-105">1003</span></span>|  
|<span data-ttu-id="54580-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="54580-106">Keywords</span></span>|<span data-ttu-id="54580-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="54580-107">WFRuntime</span></span>|  
|<span data-ttu-id="54580-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="54580-108">Level</span></span>|<span data-ttu-id="54580-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="54580-109">Information</span></span>|  
|<span data-ttu-id="54580-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="54580-110">Channel</span></span>|<span data-ttu-id="54580-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="54580-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="54580-112">Opis</span><span class="sxs-lookup"><span data-stu-id="54580-112">Description</span></span>  
 <span data-ttu-id="54580-113">Wskazuje, że wystąpienie przepływu pracy zostało zakończone; stan anulowane.</span><span class="sxs-lookup"><span data-stu-id="54580-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="54580-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="54580-114">Message</span></span>  
 <span data-ttu-id="54580-115">Obiekt WorkflowInstance o identyfikatorze: "%1" została ukończona w stan anulowane.</span><span class="sxs-lookup"><span data-stu-id="54580-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="54580-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="54580-116">Details</span></span>  
  
|<span data-ttu-id="54580-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="54580-117">Data Item Name</span></span>|<span data-ttu-id="54580-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="54580-118">Data Item Type</span></span>|<span data-ttu-id="54580-119">Opis</span><span class="sxs-lookup"><span data-stu-id="54580-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="54580-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="54580-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="54580-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="54580-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="54580-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="54580-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="54580-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="54580-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

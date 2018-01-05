---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ded4558b937a23fbe90d2bca55e6d5e4be0f0290
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="fe5c0-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="fe5c0-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="fe5c0-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fe5c0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe5c0-104">ID</span><span class="sxs-lookup"><span data-stu-id="fe5c0-104">ID</span></span>|<span data-ttu-id="fe5c0-105">1001</span><span class="sxs-lookup"><span data-stu-id="fe5c0-105">1001</span></span>|  
|<span data-ttu-id="fe5c0-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="fe5c0-106">Keywords</span></span>|<span data-ttu-id="fe5c0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fe5c0-107">WFRuntime</span></span>|  
|<span data-ttu-id="fe5c0-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="fe5c0-108">Level</span></span>|<span data-ttu-id="fe5c0-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="fe5c0-109">Information</span></span>|  
|<span data-ttu-id="fe5c0-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="fe5c0-110">Channel</span></span>|<span data-ttu-id="fe5c0-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="fe5c0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fe5c0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fe5c0-112">Description</span></span>  
 <span data-ttu-id="fe5c0-113">Wskazuje, że aplikacja przepływu pracy zostało ukończone w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="fe5c0-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fe5c0-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="fe5c0-114">Message</span></span>  
 <span data-ttu-id="fe5c0-115">Obiekt WorkflowInstance o identyfikatorze: "%1" została ukończona w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="fe5c0-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fe5c0-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="fe5c0-116">Details</span></span>  
  
|<span data-ttu-id="fe5c0-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="fe5c0-117">Data Item Name</span></span>|<span data-ttu-id="fe5c0-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="fe5c0-118">Data Item Type</span></span>|<span data-ttu-id="fe5c0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fe5c0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fe5c0-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="fe5c0-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="fe5c0-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fe5c0-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="fe5c0-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="fe5c0-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fe5c0-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fe5c0-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

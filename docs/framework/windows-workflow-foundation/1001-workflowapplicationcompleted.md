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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a62a8448319e7b07a3ea302f00f2fa269bf654ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="a0cbd-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="a0cbd-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="a0cbd-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a0cbd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0cbd-104">ID</span><span class="sxs-lookup"><span data-stu-id="a0cbd-104">ID</span></span>|<span data-ttu-id="a0cbd-105">1001</span><span class="sxs-lookup"><span data-stu-id="a0cbd-105">1001</span></span>|  
|<span data-ttu-id="a0cbd-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="a0cbd-106">Keywords</span></span>|<span data-ttu-id="a0cbd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a0cbd-107">WFRuntime</span></span>|  
|<span data-ttu-id="a0cbd-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="a0cbd-108">Level</span></span>|<span data-ttu-id="a0cbd-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="a0cbd-109">Information</span></span>|  
|<span data-ttu-id="a0cbd-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="a0cbd-110">Channel</span></span>|<span data-ttu-id="a0cbd-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="a0cbd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a0cbd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a0cbd-112">Description</span></span>  
 <span data-ttu-id="a0cbd-113">Wskazuje, że aplikacja przepływu pracy zostało ukończone w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="a0cbd-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a0cbd-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="a0cbd-114">Message</span></span>  
 <span data-ttu-id="a0cbd-115">Obiekt WorkflowInstance o identyfikatorze: "%1" została ukończona w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="a0cbd-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a0cbd-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a0cbd-116">Details</span></span>  
  
|<span data-ttu-id="a0cbd-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="a0cbd-117">Data Item Name</span></span>|<span data-ttu-id="a0cbd-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="a0cbd-118">Data Item Type</span></span>|<span data-ttu-id="a0cbd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a0cbd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a0cbd-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="a0cbd-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="a0cbd-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a0cbd-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="a0cbd-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="a0cbd-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a0cbd-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a0cbd-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

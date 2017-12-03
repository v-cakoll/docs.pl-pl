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
ms.openlocfilehash: 12b20ef893db12892636d73eeea2976f12bfccf9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="816bf-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="816bf-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="816bf-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="816bf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="816bf-104">ID</span><span class="sxs-lookup"><span data-stu-id="816bf-104">ID</span></span>|<span data-ttu-id="816bf-105">1001</span><span class="sxs-lookup"><span data-stu-id="816bf-105">1001</span></span>|  
|<span data-ttu-id="816bf-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="816bf-106">Keywords</span></span>|<span data-ttu-id="816bf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="816bf-107">WFRuntime</span></span>|  
|<span data-ttu-id="816bf-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="816bf-108">Level</span></span>|<span data-ttu-id="816bf-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="816bf-109">Information</span></span>|  
|<span data-ttu-id="816bf-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="816bf-110">Channel</span></span>|<span data-ttu-id="816bf-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="816bf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="816bf-112">Opis</span><span class="sxs-lookup"><span data-stu-id="816bf-112">Description</span></span>  
 <span data-ttu-id="816bf-113">Wskazuje, że aplikacja przepływu pracy zostało ukończone w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="816bf-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="816bf-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="816bf-114">Message</span></span>  
 <span data-ttu-id="816bf-115">Obiekt WorkflowInstance o identyfikatorze: "%1" została ukończona w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="816bf-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="816bf-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="816bf-116">Details</span></span>  
  
|<span data-ttu-id="816bf-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="816bf-117">Data Item Name</span></span>|<span data-ttu-id="816bf-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="816bf-118">Data Item Type</span></span>|<span data-ttu-id="816bf-119">Opis</span><span class="sxs-lookup"><span data-stu-id="816bf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="816bf-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="816bf-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="816bf-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="816bf-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="816bf-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="816bf-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="816bf-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="816bf-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

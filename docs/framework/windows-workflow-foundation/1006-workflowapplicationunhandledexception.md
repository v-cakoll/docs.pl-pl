---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 842d6bb6172eed5f7382633119045ea7507fb955
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="969f2-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="969f2-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="969f2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="969f2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="969f2-104">ID</span><span class="sxs-lookup"><span data-stu-id="969f2-104">ID</span></span>|<span data-ttu-id="969f2-105">1006</span><span class="sxs-lookup"><span data-stu-id="969f2-105">1006</span></span>|  
|<span data-ttu-id="969f2-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="969f2-106">Keywords</span></span>|<span data-ttu-id="969f2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="969f2-107">WFRuntime</span></span>|  
|<span data-ttu-id="969f2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="969f2-108">Level</span></span>|<span data-ttu-id="969f2-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="969f2-109">Error</span></span>|  
|<span data-ttu-id="969f2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="969f2-110">Channel</span></span>|<span data-ttu-id="969f2-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="969f2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="969f2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="969f2-112">Description</span></span>  
 <span data-ttu-id="969f2-113">Wskazuje, że aplikacja przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="969f2-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="969f2-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="969f2-114">Message</span></span>  
 <span data-ttu-id="969f2-115">Obiekt WorkflowInstance o identyfikatorze: '%1' napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="969f2-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="969f2-116">Wyjątek pochodzi z działania %2, nazwa wyświetlana: '%3'.</span><span class="sxs-lookup"><span data-stu-id="969f2-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="969f2-117">Zostanie podjęta następująca Akcja: %4.</span><span class="sxs-lookup"><span data-stu-id="969f2-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="969f2-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="969f2-118">Details</span></span>  
  
|<span data-ttu-id="969f2-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="969f2-119">Data Item Name</span></span>|<span data-ttu-id="969f2-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="969f2-120">Data Item Type</span></span>|<span data-ttu-id="969f2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="969f2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="969f2-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="969f2-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="969f2-123">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="969f2-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="969f2-124">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="969f2-124">Exception</span></span>|`xs:string`|<span data-ttu-id="969f2-125">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="969f2-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="969f2-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="969f2-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="969f2-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="969f2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

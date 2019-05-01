---
title: 1006 — WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924712"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="778e2-102">1006 — WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="778e2-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="778e2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="778e2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="778e2-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="778e2-104">ID</span></span>|<span data-ttu-id="778e2-105">1006</span><span class="sxs-lookup"><span data-stu-id="778e2-105">1006</span></span>|  
|<span data-ttu-id="778e2-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="778e2-106">Keywords</span></span>|<span data-ttu-id="778e2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="778e2-107">WFRuntime</span></span>|  
|<span data-ttu-id="778e2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="778e2-108">Level</span></span>|<span data-ttu-id="778e2-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="778e2-109">Error</span></span>|  
|<span data-ttu-id="778e2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="778e2-110">Channel</span></span>|<span data-ttu-id="778e2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="778e2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="778e2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="778e2-112">Description</span></span>  
 <span data-ttu-id="778e2-113">Wskazuje, że aplikacja przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="778e2-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="778e2-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="778e2-114">Message</span></span>  
 <span data-ttu-id="778e2-115">WorkflowInstance Id: "%1" napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="778e2-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="778e2-116">Wyjątek pochodzi z działania "%2", DisplayName: "%3".</span><span class="sxs-lookup"><span data-stu-id="778e2-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="778e2-117">Zostaną podjęte następujące działania: %4.</span><span class="sxs-lookup"><span data-stu-id="778e2-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="778e2-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="778e2-118">Details</span></span>  
  
|<span data-ttu-id="778e2-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="778e2-119">Data Item Name</span></span>|<span data-ttu-id="778e2-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="778e2-120">Data Item Type</span></span>|<span data-ttu-id="778e2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="778e2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="778e2-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="778e2-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="778e2-123">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="778e2-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="778e2-124">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="778e2-124">Exception</span></span>|`xs:string`|<span data-ttu-id="778e2-125">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="778e2-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="778e2-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="778e2-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="778e2-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="778e2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510760"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="9756a-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="9756a-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="9756a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9756a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9756a-104">ID</span><span class="sxs-lookup"><span data-stu-id="9756a-104">ID</span></span>|<span data-ttu-id="9756a-105">1006</span><span class="sxs-lookup"><span data-stu-id="9756a-105">1006</span></span>|  
|<span data-ttu-id="9756a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="9756a-106">Keywords</span></span>|<span data-ttu-id="9756a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9756a-107">WFRuntime</span></span>|  
|<span data-ttu-id="9756a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="9756a-108">Level</span></span>|<span data-ttu-id="9756a-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="9756a-109">Error</span></span>|  
|<span data-ttu-id="9756a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="9756a-110">Channel</span></span>|<span data-ttu-id="9756a-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="9756a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9756a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9756a-112">Description</span></span>  
 <span data-ttu-id="9756a-113">Wskazuje, że aplikacja przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9756a-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9756a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="9756a-114">Message</span></span>  
 <span data-ttu-id="9756a-115">Obiekt WorkflowInstance o identyfikatorze: '%1' napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9756a-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="9756a-116">Wyjątek pochodzi z działania %2, nazwa wyświetlana: '%3'.</span><span class="sxs-lookup"><span data-stu-id="9756a-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="9756a-117">Zostanie podjęta następująca Akcja: %4.</span><span class="sxs-lookup"><span data-stu-id="9756a-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9756a-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9756a-118">Details</span></span>  
  
|<span data-ttu-id="9756a-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="9756a-119">Data Item Name</span></span>|<span data-ttu-id="9756a-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="9756a-120">Data Item Type</span></span>|<span data-ttu-id="9756a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="9756a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9756a-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="9756a-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="9756a-123">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9756a-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="9756a-124">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="9756a-124">Exception</span></span>|`xs:string`|<span data-ttu-id="9756a-125">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="9756a-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="9756a-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="9756a-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9756a-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9756a-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

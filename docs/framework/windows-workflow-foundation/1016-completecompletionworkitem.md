---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="2288c-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="2288c-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2288c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2288c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2288c-104">ID</span><span class="sxs-lookup"><span data-stu-id="2288c-104">ID</span></span>|<span data-ttu-id="2288c-105">1016</span><span class="sxs-lookup"><span data-stu-id="2288c-105">1016</span></span>|  
|<span data-ttu-id="2288c-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2288c-106">Keywords</span></span>|<span data-ttu-id="2288c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2288c-107">WFRuntime</span></span>|  
|<span data-ttu-id="2288c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2288c-108">Level</span></span>|<span data-ttu-id="2288c-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="2288c-109">Verbose</span></span>|  
|<span data-ttu-id="2288c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2288c-110">Channel</span></span>|<span data-ttu-id="2288c-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="2288c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2288c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2288c-112">Description</span></span>  
 <span data-ttu-id="2288c-113">Wskazuje, że element roboczy CompletionWorkItem została ukończona.</span><span class="sxs-lookup"><span data-stu-id="2288c-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2288c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2288c-114">Message</span></span>  
 <span data-ttu-id="2288c-115">Ukończono element roboczy CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2288c-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="2288c-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="2288c-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2288c-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2288c-117">Details</span></span>  
  
|<span data-ttu-id="2288c-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2288c-118">Data Item Name</span></span>|<span data-ttu-id="2288c-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2288c-119">Data Item Type</span></span>|<span data-ttu-id="2288c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2288c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2288c-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2288c-121">ParentActivity</span></span>|<span data-ttu-id="2288c-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="2288c-122">xs:string</span></span>|<span data-ttu-id="2288c-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2288c-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="2288c-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="2288c-124">ParentDisplayName</span></span>|<span data-ttu-id="2288c-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="2288c-125">xs:string</span></span>|<span data-ttu-id="2288c-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2288c-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="2288c-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="2288c-127">ParentInstanceId</span></span>|<span data-ttu-id="2288c-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="2288c-128">xs:string</span></span>|<span data-ttu-id="2288c-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2288c-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="2288c-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="2288c-130">CompletedActivity</span></span>|<span data-ttu-id="2288c-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="2288c-131">xs:string</span></span>|<span data-ttu-id="2288c-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="2288c-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="2288c-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2288c-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="2288c-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="2288c-134">xs:string</span></span>|<span data-ttu-id="2288c-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="2288c-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="2288c-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2288c-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="2288c-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="2288c-137">xs:string</span></span>|<span data-ttu-id="2288c-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="2288c-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="2288c-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="2288c-139">AppDomain</span></span>|<span data-ttu-id="2288c-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="2288c-140">xs:string</span></span>|<span data-ttu-id="2288c-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2288c-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1016 — CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925089"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="3adcd-102">1016 — CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="3adcd-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3adcd-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3adcd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3adcd-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="3adcd-104">ID</span></span>|<span data-ttu-id="3adcd-105">1016</span><span class="sxs-lookup"><span data-stu-id="3adcd-105">1016</span></span>|  
|<span data-ttu-id="3adcd-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3adcd-106">Keywords</span></span>|<span data-ttu-id="3adcd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3adcd-107">WFRuntime</span></span>|  
|<span data-ttu-id="3adcd-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="3adcd-108">Level</span></span>|<span data-ttu-id="3adcd-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="3adcd-109">Verbose</span></span>|  
|<span data-ttu-id="3adcd-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="3adcd-110">Channel</span></span>|<span data-ttu-id="3adcd-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3adcd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3adcd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3adcd-112">Description</span></span>  
 <span data-ttu-id="3adcd-113">Wskazuje, że CompletionWorkItem zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="3adcd-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3adcd-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="3adcd-114">Message</span></span>  
 <span data-ttu-id="3adcd-115">CompletionWorkItem zostało ukończone dla nadrzędnej działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="3adcd-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="3adcd-116">Ukończono %4, DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="3adcd-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3adcd-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3adcd-117">Details</span></span>  
  
|<span data-ttu-id="3adcd-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="3adcd-118">Data Item Name</span></span>|<span data-ttu-id="3adcd-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="3adcd-119">Data Item Type</span></span>|<span data-ttu-id="3adcd-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3adcd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3adcd-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3adcd-121">ParentActivity</span></span>|<span data-ttu-id="3adcd-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="3adcd-122">xs:string</span></span>|<span data-ttu-id="3adcd-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3adcd-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="3adcd-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="3adcd-124">ParentDisplayName</span></span>|<span data-ttu-id="3adcd-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="3adcd-125">xs:string</span></span>|<span data-ttu-id="3adcd-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3adcd-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="3adcd-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="3adcd-127">ParentInstanceId</span></span>|<span data-ttu-id="3adcd-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="3adcd-128">xs:string</span></span>|<span data-ttu-id="3adcd-129">Identyfikator wystąpienia działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3adcd-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="3adcd-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="3adcd-130">CompletedActivity</span></span>|<span data-ttu-id="3adcd-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="3adcd-131">xs:string</span></span>|<span data-ttu-id="3adcd-132">Nazwa typu zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="3adcd-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="3adcd-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3adcd-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="3adcd-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="3adcd-134">xs:string</span></span>|<span data-ttu-id="3adcd-135">Nazwa wyświetlana zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="3adcd-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="3adcd-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3adcd-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="3adcd-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="3adcd-137">xs:string</span></span>|<span data-ttu-id="3adcd-138">Identyfikator wystąpienia zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="3adcd-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="3adcd-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3adcd-139">AppDomain</span></span>|<span data-ttu-id="3adcd-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="3adcd-140">xs:string</span></span>|<span data-ttu-id="3adcd-141">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3adcd-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

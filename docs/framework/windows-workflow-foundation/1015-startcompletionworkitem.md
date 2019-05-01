---
title: 1015 — StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032269"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="8fb8d-102">1015 — StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="8fb8d-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8fb8d-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8fb8d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8fb8d-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8fb8d-104">ID</span></span>|<span data-ttu-id="8fb8d-105">1015</span><span class="sxs-lookup"><span data-stu-id="8fb8d-105">1015</span></span>|  
|<span data-ttu-id="8fb8d-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8fb8d-106">Keywords</span></span>|<span data-ttu-id="8fb8d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8fb8d-107">WFRuntime</span></span>|  
|<span data-ttu-id="8fb8d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8fb8d-108">Level</span></span>|<span data-ttu-id="8fb8d-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="8fb8d-109">Verbose</span></span>|  
|<span data-ttu-id="8fb8d-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8fb8d-110">Channel</span></span>|<span data-ttu-id="8fb8d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8fb8d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8fb8d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8fb8d-112">Description</span></span>  
 <span data-ttu-id="8fb8d-113">Wskazuje, że CompletionWorkItem Trwa uruchamianie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8fb8d-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8fb8d-114">Message</span></span>  
 <span data-ttu-id="8fb8d-115">Rozpoczynanie wykonywania CompletionWorkItem dla nadrzędnego działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="8fb8d-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="8fb8d-116">Ukończono %4, DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8fb8d-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8fb8d-117">Details</span></span>  
  
|<span data-ttu-id="8fb8d-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8fb8d-118">Data Item Name</span></span>|<span data-ttu-id="8fb8d-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8fb8d-119">Data Item Type</span></span>|<span data-ttu-id="8fb8d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="8fb8d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8fb8d-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8fb8d-121">ParentActivity</span></span>|<span data-ttu-id="8fb8d-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="8fb8d-122">xs:string</span></span>|<span data-ttu-id="8fb8d-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="8fb8d-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="8fb8d-124">ParentDisplayName</span></span>|<span data-ttu-id="8fb8d-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="8fb8d-125">xs:string</span></span>|<span data-ttu-id="8fb8d-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="8fb8d-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="8fb8d-127">ParentInstanceId</span></span>|<span data-ttu-id="8fb8d-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="8fb8d-128">xs:string</span></span>|<span data-ttu-id="8fb8d-129">Identyfikator wystąpienia działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="8fb8d-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="8fb8d-130">CompletedActivity</span></span>|<span data-ttu-id="8fb8d-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="8fb8d-131">xs:string</span></span>|<span data-ttu-id="8fb8d-132">Nazwa typu zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="8fb8d-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8fb8d-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="8fb8d-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="8fb8d-134">xs:string</span></span>|<span data-ttu-id="8fb8d-135">Nazwa wyświetlana zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="8fb8d-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8fb8d-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="8fb8d-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="8fb8d-137">xs:string</span></span>|<span data-ttu-id="8fb8d-138">Identyfikator wystąpienia zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="8fb8d-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8fb8d-139">AppDomain</span></span>|<span data-ttu-id="8fb8d-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="8fb8d-140">xs:string</span></span>|<span data-ttu-id="8fb8d-141">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8fb8d-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

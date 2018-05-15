---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="7f077-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="7f077-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7f077-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7f077-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f077-104">ID</span><span class="sxs-lookup"><span data-stu-id="7f077-104">ID</span></span>|<span data-ttu-id="7f077-105">1015</span><span class="sxs-lookup"><span data-stu-id="7f077-105">1015</span></span>|  
|<span data-ttu-id="7f077-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7f077-106">Keywords</span></span>|<span data-ttu-id="7f077-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7f077-107">WFRuntime</span></span>|  
|<span data-ttu-id="7f077-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7f077-108">Level</span></span>|<span data-ttu-id="7f077-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="7f077-109">Verbose</span></span>|  
|<span data-ttu-id="7f077-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7f077-110">Channel</span></span>|<span data-ttu-id="7f077-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="7f077-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7f077-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7f077-112">Description</span></span>  
 <span data-ttu-id="7f077-113">Wskazuje, że element roboczy CompletionWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7f077-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7f077-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7f077-114">Message</span></span>  
 <span data-ttu-id="7f077-115">Rozpoczęcie wykonywania elementu roboczego CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="7f077-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="7f077-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="7f077-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7f077-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7f077-117">Details</span></span>  
  
|<span data-ttu-id="7f077-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7f077-118">Data Item Name</span></span>|<span data-ttu-id="7f077-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7f077-119">Data Item Type</span></span>|<span data-ttu-id="7f077-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7f077-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7f077-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f077-121">ParentActivity</span></span>|<span data-ttu-id="7f077-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="7f077-122">xs:string</span></span>|<span data-ttu-id="7f077-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="7f077-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="7f077-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="7f077-124">ParentDisplayName</span></span>|<span data-ttu-id="7f077-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="7f077-125">xs:string</span></span>|<span data-ttu-id="7f077-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="7f077-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="7f077-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="7f077-127">ParentInstanceId</span></span>|<span data-ttu-id="7f077-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="7f077-128">xs:string</span></span>|<span data-ttu-id="7f077-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="7f077-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="7f077-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="7f077-130">CompletedActivity</span></span>|<span data-ttu-id="7f077-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="7f077-131">xs:string</span></span>|<span data-ttu-id="7f077-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="7f077-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="7f077-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="7f077-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="7f077-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="7f077-134">xs:string</span></span>|<span data-ttu-id="7f077-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="7f077-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="7f077-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="7f077-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="7f077-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="7f077-137">xs:string</span></span>|<span data-ttu-id="7f077-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="7f077-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="7f077-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="7f077-139">AppDomain</span></span>|<span data-ttu-id="7f077-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="7f077-140">xs:string</span></span>|<span data-ttu-id="7f077-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7f077-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="3fc0a-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="3fc0a-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3fc0a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3fc0a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3fc0a-104">ID</span><span class="sxs-lookup"><span data-stu-id="3fc0a-104">ID</span></span>|<span data-ttu-id="3fc0a-105">1014</span><span class="sxs-lookup"><span data-stu-id="3fc0a-105">1014</span></span>|  
|<span data-ttu-id="3fc0a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3fc0a-106">Keywords</span></span>|<span data-ttu-id="3fc0a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3fc0a-107">WFRuntime</span></span>|  
|<span data-ttu-id="3fc0a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="3fc0a-108">Level</span></span>|<span data-ttu-id="3fc0a-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="3fc0a-109">Verbose</span></span>|  
|<span data-ttu-id="3fc0a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="3fc0a-110">Channel</span></span>|<span data-ttu-id="3fc0a-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="3fc0a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3fc0a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3fc0a-112">Description</span></span>  
 <span data-ttu-id="3fc0a-113">Wskazuje, że zaplanowano element roboczy CompletionWorkItem.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3fc0a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="3fc0a-114">Message</span></span>  
 <span data-ttu-id="3fc0a-115">Zaplanowano element roboczy CompletionWorkItem dla działania nadrzędnego %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="3fc0a-116">Ukończono %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3fc0a-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3fc0a-117">Details</span></span>  
  
|<span data-ttu-id="3fc0a-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="3fc0a-118">Data Item Name</span></span>|<span data-ttu-id="3fc0a-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="3fc0a-119">Data Item Type</span></span>|<span data-ttu-id="3fc0a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3fc0a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3fc0a-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3fc0a-121">ParentActivity</span></span>|<span data-ttu-id="3fc0a-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="3fc0a-122">xs:string</span></span>|<span data-ttu-id="3fc0a-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="3fc0a-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="3fc0a-124">ParentDisplayName</span></span>|<span data-ttu-id="3fc0a-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="3fc0a-125">xs:string</span></span>|<span data-ttu-id="3fc0a-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="3fc0a-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="3fc0a-127">ParentInstanceId</span></span>|<span data-ttu-id="3fc0a-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="3fc0a-128">xs:string</span></span>|<span data-ttu-id="3fc0a-129">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="3fc0a-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="3fc0a-130">CompletedActivity</span></span>|<span data-ttu-id="3fc0a-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="3fc0a-131">xs:string</span></span>|<span data-ttu-id="3fc0a-132">Nazwa typu działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="3fc0a-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="3fc0a-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="3fc0a-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="3fc0a-134">xs:string</span></span>|<span data-ttu-id="3fc0a-135">Nazwa wyświetlana ukończonego działania.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="3fc0a-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="3fc0a-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="3fc0a-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="3fc0a-137">xs:string</span></span>|<span data-ttu-id="3fc0a-138">Identyfikator wystąpienia działania ukończone.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="3fc0a-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="3fc0a-139">AppDomain</span></span>|<span data-ttu-id="3fc0a-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="3fc0a-140">xs:string</span></span>|<span data-ttu-id="3fc0a-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3fc0a-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

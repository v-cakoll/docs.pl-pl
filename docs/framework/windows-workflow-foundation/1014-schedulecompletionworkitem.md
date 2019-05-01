---
title: 1014 — ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982270"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="21d74-102">1014 — ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="21d74-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="21d74-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="21d74-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21d74-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="21d74-104">ID</span></span>|<span data-ttu-id="21d74-105">1014</span><span class="sxs-lookup"><span data-stu-id="21d74-105">1014</span></span>|  
|<span data-ttu-id="21d74-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="21d74-106">Keywords</span></span>|<span data-ttu-id="21d74-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="21d74-107">WFRuntime</span></span>|  
|<span data-ttu-id="21d74-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="21d74-108">Level</span></span>|<span data-ttu-id="21d74-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="21d74-109">Verbose</span></span>|  
|<span data-ttu-id="21d74-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="21d74-110">Channel</span></span>|<span data-ttu-id="21d74-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="21d74-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21d74-112">Opis</span><span class="sxs-lookup"><span data-stu-id="21d74-112">Description</span></span>  
 <span data-ttu-id="21d74-113">Wskazuje, że CompletionWorkItem została zaplanowana.</span><span class="sxs-lookup"><span data-stu-id="21d74-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21d74-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="21d74-114">Message</span></span>  
 <span data-ttu-id="21d74-115">CompletionWorkItem zaplanowano nadrzędnego działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="21d74-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="21d74-116">Ukończono %4, DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="21d74-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21d74-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="21d74-117">Details</span></span>  
  
|<span data-ttu-id="21d74-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="21d74-118">Data Item Name</span></span>|<span data-ttu-id="21d74-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="21d74-119">Data Item Type</span></span>|<span data-ttu-id="21d74-120">Opis</span><span class="sxs-lookup"><span data-stu-id="21d74-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21d74-121">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="21d74-121">ParentActivity</span></span>|<span data-ttu-id="21d74-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="21d74-122">xs:string</span></span>|<span data-ttu-id="21d74-123">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="21d74-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="21d74-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="21d74-124">ParentDisplayName</span></span>|<span data-ttu-id="21d74-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="21d74-125">xs:string</span></span>|<span data-ttu-id="21d74-126">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="21d74-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="21d74-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="21d74-127">ParentInstanceId</span></span>|<span data-ttu-id="21d74-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="21d74-128">xs:string</span></span>|<span data-ttu-id="21d74-129">Identyfikator wystąpienia działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="21d74-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="21d74-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="21d74-130">CompletedActivity</span></span>|<span data-ttu-id="21d74-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="21d74-131">xs:string</span></span>|<span data-ttu-id="21d74-132">Nazwa typu zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="21d74-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="21d74-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="21d74-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="21d74-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="21d74-134">xs:string</span></span>|<span data-ttu-id="21d74-135">Nazwa wyświetlana zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="21d74-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="21d74-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="21d74-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="21d74-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="21d74-137">xs:string</span></span>|<span data-ttu-id="21d74-138">Identyfikator wystąpienia zakończonego działania.</span><span class="sxs-lookup"><span data-stu-id="21d74-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="21d74-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="21d74-139">AppDomain</span></span>|<span data-ttu-id="21d74-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="21d74-140">xs:string</span></span>|<span data-ttu-id="21d74-141">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="21d74-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

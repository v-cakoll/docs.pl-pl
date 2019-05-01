---
title: 1021 — ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924426"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="e9d97-102">1021 — ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="e9d97-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e9d97-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e9d97-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9d97-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e9d97-104">ID</span></span>|<span data-ttu-id="e9d97-105">1021</span><span class="sxs-lookup"><span data-stu-id="e9d97-105">1021</span></span>|  
|<span data-ttu-id="e9d97-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e9d97-106">Keywords</span></span>|<span data-ttu-id="e9d97-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e9d97-107">WFRuntime</span></span>|  
|<span data-ttu-id="e9d97-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e9d97-108">Level</span></span>|<span data-ttu-id="e9d97-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="e9d97-109">Verbose</span></span>|  
|<span data-ttu-id="e9d97-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e9d97-110">Channel</span></span>|<span data-ttu-id="e9d97-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e9d97-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e9d97-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e9d97-112">Description</span></span>  
 <span data-ttu-id="e9d97-113">Wskazuje, że BookmarkWorkItem została zaplanowana.</span><span class="sxs-lookup"><span data-stu-id="e9d97-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e9d97-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e9d97-114">Message</span></span>  
 <span data-ttu-id="e9d97-115">BookmarkWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="e9d97-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="e9d97-116">Nazwa_zakładki: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="e9d97-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e9d97-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e9d97-117">Details</span></span>  
  
|<span data-ttu-id="e9d97-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e9d97-118">Data Item Name</span></span>|<span data-ttu-id="e9d97-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e9d97-119">Data Item Type</span></span>|<span data-ttu-id="e9d97-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e9d97-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e9d97-121">Działanie</span><span class="sxs-lookup"><span data-stu-id="e9d97-121">Activity</span></span>|<span data-ttu-id="e9d97-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9d97-122">xs:string</span></span>|<span data-ttu-id="e9d97-123">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="e9d97-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="e9d97-124">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="e9d97-124">DisplayName</span></span>|<span data-ttu-id="e9d97-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9d97-125">xs:string</span></span>|<span data-ttu-id="e9d97-126">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="e9d97-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="e9d97-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e9d97-127">InstanceId</span></span>|<span data-ttu-id="e9d97-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9d97-128">xs:string</span></span>|<span data-ttu-id="e9d97-129">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="e9d97-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e9d97-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="e9d97-130">BookmarkName</span></span>|<span data-ttu-id="e9d97-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9d97-131">xs:string</span></span>|<span data-ttu-id="e9d97-132">Nazwa zakładki.</span><span class="sxs-lookup"><span data-stu-id="e9d97-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="e9d97-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="e9d97-133">BookmarkScope</span></span>|<span data-ttu-id="e9d97-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9d97-134">xs:string</span></span>|<span data-ttu-id="e9d97-135">Zakres zakładki.</span><span class="sxs-lookup"><span data-stu-id="e9d97-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="e9d97-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e9d97-136">AppDomain</span></span>|<span data-ttu-id="e9d97-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="e9d97-137">xs:string</span></span>|<span data-ttu-id="e9d97-138">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e9d97-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

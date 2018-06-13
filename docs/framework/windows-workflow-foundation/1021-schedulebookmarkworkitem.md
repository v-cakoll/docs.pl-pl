---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509759"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="c60cf-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="c60cf-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c60cf-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c60cf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c60cf-104">ID</span><span class="sxs-lookup"><span data-stu-id="c60cf-104">ID</span></span>|<span data-ttu-id="c60cf-105">1021</span><span class="sxs-lookup"><span data-stu-id="c60cf-105">1021</span></span>|  
|<span data-ttu-id="c60cf-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c60cf-106">Keywords</span></span>|<span data-ttu-id="c60cf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c60cf-107">WFRuntime</span></span>|  
|<span data-ttu-id="c60cf-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c60cf-108">Level</span></span>|<span data-ttu-id="c60cf-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="c60cf-109">Verbose</span></span>|  
|<span data-ttu-id="c60cf-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c60cf-110">Channel</span></span>|<span data-ttu-id="c60cf-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="c60cf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c60cf-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c60cf-112">Description</span></span>  
 <span data-ttu-id="c60cf-113">Wskazuje, że zaplanowano element roboczy BookmarkWorkItem.</span><span class="sxs-lookup"><span data-stu-id="c60cf-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c60cf-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c60cf-114">Message</span></span>  
 <span data-ttu-id="c60cf-115">Zaplanowano element roboczy BookmarkWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c60cf-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="c60cf-116">Nazwa zakładki: %4, zakres zakładek: %5.</span><span class="sxs-lookup"><span data-stu-id="c60cf-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c60cf-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c60cf-117">Details</span></span>  
  
|<span data-ttu-id="c60cf-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c60cf-118">Data Item Name</span></span>|<span data-ttu-id="c60cf-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c60cf-119">Data Item Type</span></span>|<span data-ttu-id="c60cf-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c60cf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c60cf-121">Działanie</span><span class="sxs-lookup"><span data-stu-id="c60cf-121">Activity</span></span>|<span data-ttu-id="c60cf-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="c60cf-122">xs:string</span></span>|<span data-ttu-id="c60cf-123">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="c60cf-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="c60cf-124">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="c60cf-124">DisplayName</span></span>|<span data-ttu-id="c60cf-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="c60cf-125">xs:string</span></span>|<span data-ttu-id="c60cf-126">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="c60cf-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="c60cf-127">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="c60cf-127">InstanceId</span></span>|<span data-ttu-id="c60cf-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="c60cf-128">xs:string</span></span>|<span data-ttu-id="c60cf-129">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="c60cf-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c60cf-130">Nazwa zakładki</span><span class="sxs-lookup"><span data-stu-id="c60cf-130">BookmarkName</span></span>|<span data-ttu-id="c60cf-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="c60cf-131">xs:string</span></span>|<span data-ttu-id="c60cf-132">Nazwa zakładki.</span><span class="sxs-lookup"><span data-stu-id="c60cf-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="c60cf-133">Zakres zakładek</span><span class="sxs-lookup"><span data-stu-id="c60cf-133">BookmarkScope</span></span>|<span data-ttu-id="c60cf-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="c60cf-134">xs:string</span></span>|<span data-ttu-id="c60cf-135">Zakres zakładki.</span><span class="sxs-lookup"><span data-stu-id="c60cf-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="c60cf-136">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c60cf-136">AppDomain</span></span>|<span data-ttu-id="c60cf-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="c60cf-137">xs:string</span></span>|<span data-ttu-id="c60cf-138">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c60cf-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

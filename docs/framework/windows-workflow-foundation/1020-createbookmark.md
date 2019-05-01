---
title: 1020 — CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924751"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="179b2-102">1020 — CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="179b2-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="179b2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="179b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="179b2-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="179b2-104">ID</span></span>|<span data-ttu-id="179b2-105">1020</span><span class="sxs-lookup"><span data-stu-id="179b2-105">1020</span></span>|  
|<span data-ttu-id="179b2-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="179b2-106">Keywords</span></span>|<span data-ttu-id="179b2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="179b2-107">WFRuntime</span></span>|  
|<span data-ttu-id="179b2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="179b2-108">Level</span></span>|<span data-ttu-id="179b2-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="179b2-109">Verbose</span></span>|  
|<span data-ttu-id="179b2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="179b2-110">Channel</span></span>|<span data-ttu-id="179b2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="179b2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="179b2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="179b2-112">Description</span></span>  
 <span data-ttu-id="179b2-113">Wskazuje, że utworzono zakładki działania.</span><span class="sxs-lookup"><span data-stu-id="179b2-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="179b2-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="179b2-114">Message</span></span>  
 <span data-ttu-id="179b2-115">Zakładka została utworzona dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="179b2-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="179b2-116">Nazwa_zakładki: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="179b2-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="179b2-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="179b2-117">Details</span></span>  
  
|<span data-ttu-id="179b2-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="179b2-118">Data Item Name</span></span>|<span data-ttu-id="179b2-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="179b2-119">Data Item Type</span></span>|<span data-ttu-id="179b2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="179b2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="179b2-121">Działanie</span><span class="sxs-lookup"><span data-stu-id="179b2-121">Activity</span></span>|<span data-ttu-id="179b2-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="179b2-122">xs:string</span></span>|<span data-ttu-id="179b2-123">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="179b2-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="179b2-124">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="179b2-124">DisplayName</span></span>|<span data-ttu-id="179b2-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="179b2-125">xs:string</span></span>|<span data-ttu-id="179b2-126">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="179b2-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="179b2-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="179b2-127">InstanceId</span></span>|<span data-ttu-id="179b2-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="179b2-128">xs:string</span></span>|<span data-ttu-id="179b2-129">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="179b2-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="179b2-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="179b2-130">BookmarkName</span></span>|<span data-ttu-id="179b2-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="179b2-131">xs:string</span></span>|<span data-ttu-id="179b2-132">Nazwa zakładki.</span><span class="sxs-lookup"><span data-stu-id="179b2-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="179b2-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="179b2-133">BookmarkScope</span></span>|<span data-ttu-id="179b2-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="179b2-134">xs:string</span></span>|<span data-ttu-id="179b2-135">Zakres zakładki.</span><span class="sxs-lookup"><span data-stu-id="179b2-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="179b2-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="179b2-136">AppDomain</span></span>|<span data-ttu-id="179b2-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="179b2-137">xs:string</span></span>|<span data-ttu-id="179b2-138">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="179b2-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

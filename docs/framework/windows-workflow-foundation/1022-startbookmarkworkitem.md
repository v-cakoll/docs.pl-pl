---
title: 1022 — StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 93d906b32b51effaa709da6763f535708cd6f821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924725"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="87d8f-102">1022 — StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="87d8f-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="87d8f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="87d8f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="87d8f-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="87d8f-104">ID</span></span>|<span data-ttu-id="87d8f-105">1022</span><span class="sxs-lookup"><span data-stu-id="87d8f-105">1022</span></span>|  
|<span data-ttu-id="87d8f-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="87d8f-106">Keywords</span></span>|<span data-ttu-id="87d8f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="87d8f-107">WFRuntime</span></span>|  
|<span data-ttu-id="87d8f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="87d8f-108">Level</span></span>|<span data-ttu-id="87d8f-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="87d8f-109">Verbose</span></span>|  
|<span data-ttu-id="87d8f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="87d8f-110">Channel</span></span>|<span data-ttu-id="87d8f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="87d8f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="87d8f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="87d8f-112">Description</span></span>  
 <span data-ttu-id="87d8f-113">Wskazuje, że BookmarkWorkItem Trwa uruchamianie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="87d8f-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="87d8f-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="87d8f-114">Message</span></span>  
 <span data-ttu-id="87d8f-115">Rozpoczynanie wykonywania BookmarkWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="87d8f-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="87d8f-116">Nazwa_zakładki: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="87d8f-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="87d8f-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="87d8f-117">Details</span></span>  
  
|<span data-ttu-id="87d8f-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="87d8f-118">Data Item Name</span></span>|<span data-ttu-id="87d8f-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="87d8f-119">Data Item Type</span></span>|<span data-ttu-id="87d8f-120">Opis</span><span class="sxs-lookup"><span data-stu-id="87d8f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="87d8f-121">Działanie</span><span class="sxs-lookup"><span data-stu-id="87d8f-121">Activity</span></span>|<span data-ttu-id="87d8f-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="87d8f-122">xs:string</span></span>|<span data-ttu-id="87d8f-123">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="87d8f-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="87d8f-124">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="87d8f-124">DisplayName</span></span>|<span data-ttu-id="87d8f-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="87d8f-125">xs:string</span></span>|<span data-ttu-id="87d8f-126">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="87d8f-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="87d8f-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="87d8f-127">InstanceId</span></span>|<span data-ttu-id="87d8f-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="87d8f-128">xs:string</span></span>|<span data-ttu-id="87d8f-129">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="87d8f-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="87d8f-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="87d8f-130">BookmarkName</span></span>|<span data-ttu-id="87d8f-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="87d8f-131">xs:string</span></span>|<span data-ttu-id="87d8f-132">Nazwa zakładki.</span><span class="sxs-lookup"><span data-stu-id="87d8f-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="87d8f-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="87d8f-133">BookmarkScope</span></span>|<span data-ttu-id="87d8f-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="87d8f-134">xs:string</span></span>|<span data-ttu-id="87d8f-135">Zakres zakładki.</span><span class="sxs-lookup"><span data-stu-id="87d8f-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="87d8f-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="87d8f-136">AppDomain</span></span>|<span data-ttu-id="87d8f-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="87d8f-137">xs:string</span></span>|<span data-ttu-id="87d8f-138">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="87d8f-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

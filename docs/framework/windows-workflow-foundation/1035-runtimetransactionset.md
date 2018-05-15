---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="d42d8-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="d42d8-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="d42d8-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d42d8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d42d8-104">ID</span><span class="sxs-lookup"><span data-stu-id="d42d8-104">ID</span></span>|<span data-ttu-id="d42d8-105">1035</span><span class="sxs-lookup"><span data-stu-id="d42d8-105">1035</span></span>|  
|<span data-ttu-id="d42d8-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d42d8-106">Keywords</span></span>|<span data-ttu-id="d42d8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d42d8-107">WFRuntime</span></span>|  
|<span data-ttu-id="d42d8-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d42d8-108">Level</span></span>|<span data-ttu-id="d42d8-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="d42d8-109">Verbose</span></span>|  
|<span data-ttu-id="d42d8-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d42d8-110">Channel</span></span>|<span data-ttu-id="d42d8-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="d42d8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d42d8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d42d8-112">Description</span></span>  
 <span data-ttu-id="d42d8-113">Wskazuje, że działanie ustawił transakcja czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d42d8-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d42d8-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d42d8-114">Message</span></span>  
 <span data-ttu-id="d42d8-115">Transakcja czasu wykonywania została ustawiona przez działanie %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d42d8-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="d42d8-116">Wykonanie izolowane, ograniczone do działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="d42d8-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d42d8-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d42d8-117">Details</span></span>  
  
|<span data-ttu-id="d42d8-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d42d8-118">Data Item Name</span></span>|<span data-ttu-id="d42d8-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d42d8-119">Data Item Type</span></span>|<span data-ttu-id="d42d8-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d42d8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d42d8-121">Działanie</span><span class="sxs-lookup"><span data-stu-id="d42d8-121">Activity</span></span>|<span data-ttu-id="d42d8-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="d42d8-122">xs:string</span></span>|<span data-ttu-id="d42d8-123">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="d42d8-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="d42d8-124">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="d42d8-124">DisplayName</span></span>|<span data-ttu-id="d42d8-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="d42d8-125">xs:string</span></span>|<span data-ttu-id="d42d8-126">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="d42d8-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="d42d8-127">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="d42d8-127">InstanceId</span></span>|<span data-ttu-id="d42d8-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="d42d8-128">xs:string</span></span>|<span data-ttu-id="d42d8-129">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="d42d8-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d42d8-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="d42d8-130">IsolatedActivity</span></span>|<span data-ttu-id="d42d8-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="d42d8-131">xs:string</span></span>|<span data-ttu-id="d42d8-132">Nazwa typu transakcji jest izolowane, ograniczone do działania.</span><span class="sxs-lookup"><span data-stu-id="d42d8-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="d42d8-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="d42d8-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="d42d8-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="d42d8-134">xs:string</span></span>|<span data-ttu-id="d42d8-135">Nazwa wyświetlana transakcji jest izolowane, ograniczone do działania.</span><span class="sxs-lookup"><span data-stu-id="d42d8-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="d42d8-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="d42d8-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="d42d8-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="d42d8-137">xs:string</span></span>|<span data-ttu-id="d42d8-138">Identyfikator wystąpienia transakcji jest izolowane, ograniczone do działania.</span><span class="sxs-lookup"><span data-stu-id="d42d8-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="d42d8-139">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d42d8-139">AppDomain</span></span>|<span data-ttu-id="d42d8-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="d42d8-140">xs:string</span></span>|<span data-ttu-id="d42d8-141">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d42d8-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509975"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="023bb-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="023bb-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="023bb-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="023bb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="023bb-104">ID</span><span class="sxs-lookup"><span data-stu-id="023bb-104">ID</span></span>|<span data-ttu-id="023bb-105">1009</span><span class="sxs-lookup"><span data-stu-id="023bb-105">1009</span></span>|  
|<span data-ttu-id="023bb-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="023bb-106">Keywords</span></span>|<span data-ttu-id="023bb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="023bb-107">WFRuntime</span></span>|  
|<span data-ttu-id="023bb-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="023bb-108">Level</span></span>|<span data-ttu-id="023bb-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="023bb-109">Information</span></span>|  
|<span data-ttu-id="023bb-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="023bb-110">Channel</span></span>|<span data-ttu-id="023bb-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="023bb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="023bb-112">Opis</span><span class="sxs-lookup"><span data-stu-id="023bb-112">Description</span></span>  
 <span data-ttu-id="023bb-113">Wskazuje, że działanie jest zaplanowane co do wykonania.</span><span class="sxs-lookup"><span data-stu-id="023bb-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="023bb-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="023bb-114">Message</span></span>  
 <span data-ttu-id="023bb-115">Działanie "%1", nazwa wyświetlana nadrzędne: "%2", identyfikator wystąpienia: '%3' zaplanowało działanie podrzędne %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.</span><span class="sxs-lookup"><span data-stu-id="023bb-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="023bb-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="023bb-116">Details</span></span>  
  
|<span data-ttu-id="023bb-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="023bb-117">Data Item Name</span></span>|<span data-ttu-id="023bb-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="023bb-118">Data Item Type</span></span>|<span data-ttu-id="023bb-119">Opis</span><span class="sxs-lookup"><span data-stu-id="023bb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="023bb-120">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="023bb-120">ParentActivity</span></span>|<span data-ttu-id="023bb-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="023bb-121">xs:string</span></span>|<span data-ttu-id="023bb-122">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="023bb-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="023bb-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="023bb-123">ParentDisplayName</span></span>|<span data-ttu-id="023bb-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="023bb-124">xs:string</span></span>|<span data-ttu-id="023bb-125">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="023bb-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="023bb-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="023bb-126">ParentInstanceId</span></span>|<span data-ttu-id="023bb-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="023bb-127">xs:string</span></span>|<span data-ttu-id="023bb-128">Identyfikator wystąpienia działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="023bb-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="023bb-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="023bb-129">ChildActivity</span></span>|<span data-ttu-id="023bb-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="023bb-130">xs:string</span></span>|<span data-ttu-id="023bb-131">Nazwa typu działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="023bb-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="023bb-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="023bb-132">ChildDisplayName</span></span>|<span data-ttu-id="023bb-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="023bb-133">xs:string</span></span>|<span data-ttu-id="023bb-134">Nazwa wyświetlana działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="023bb-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="023bb-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="023bb-135">ChildInstanceId</span></span>|<span data-ttu-id="023bb-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="023bb-136">xs:string</span></span>|<span data-ttu-id="023bb-137">Identyfikator wystąpienia działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="023bb-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="023bb-138">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="023bb-138">AppDomain</span></span>|<span data-ttu-id="023bb-139">xs:String</span><span class="sxs-lookup"><span data-stu-id="023bb-139">xs:string</span></span>|<span data-ttu-id="023bb-140">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="023bb-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

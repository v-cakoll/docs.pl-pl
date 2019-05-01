---
title: 1009 — ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924660"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="8c01b-102">1009 — ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="8c01b-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="8c01b-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8c01b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c01b-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8c01b-104">ID</span></span>|<span data-ttu-id="8c01b-105">1009</span><span class="sxs-lookup"><span data-stu-id="8c01b-105">1009</span></span>|  
|<span data-ttu-id="8c01b-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8c01b-106">Keywords</span></span>|<span data-ttu-id="8c01b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8c01b-107">WFRuntime</span></span>|  
|<span data-ttu-id="8c01b-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8c01b-108">Level</span></span>|<span data-ttu-id="8c01b-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="8c01b-109">Information</span></span>|  
|<span data-ttu-id="8c01b-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8c01b-110">Channel</span></span>|<span data-ttu-id="8c01b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8c01b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c01b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8c01b-112">Description</span></span>  
 <span data-ttu-id="8c01b-113">Wskazuje, że działanie jest zaplanowane do wykonania.</span><span class="sxs-lookup"><span data-stu-id="8c01b-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c01b-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8c01b-114">Message</span></span>  
 <span data-ttu-id="8c01b-115">Nadrzędne działanie "%1", DisplayName: "%2", InstanceId: "%3" podrzędnych zaplanowanego działania "%4" DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="8c01b-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c01b-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8c01b-116">Details</span></span>  
  
|<span data-ttu-id="8c01b-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8c01b-117">Data Item Name</span></span>|<span data-ttu-id="8c01b-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8c01b-118">Data Item Type</span></span>|<span data-ttu-id="8c01b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8c01b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8c01b-120">Działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8c01b-120">ParentActivity</span></span>|<span data-ttu-id="8c01b-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="8c01b-121">xs:string</span></span>|<span data-ttu-id="8c01b-122">Nazwa typu działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8c01b-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="8c01b-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="8c01b-123">ParentDisplayName</span></span>|<span data-ttu-id="8c01b-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="8c01b-124">xs:string</span></span>|<span data-ttu-id="8c01b-125">Nazwa wyświetlana działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8c01b-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="8c01b-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="8c01b-126">ParentInstanceId</span></span>|<span data-ttu-id="8c01b-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="8c01b-127">xs:string</span></span>|<span data-ttu-id="8c01b-128">Identyfikator wystąpienia działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8c01b-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="8c01b-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="8c01b-129">ChildActivity</span></span>|<span data-ttu-id="8c01b-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="8c01b-130">xs:string</span></span>|<span data-ttu-id="8c01b-131">Nazwa typu działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="8c01b-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="8c01b-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="8c01b-132">ChildDisplayName</span></span>|<span data-ttu-id="8c01b-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="8c01b-133">xs:string</span></span>|<span data-ttu-id="8c01b-134">Nazwa wyświetlana działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="8c01b-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="8c01b-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="8c01b-135">ChildInstanceId</span></span>|<span data-ttu-id="8c01b-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="8c01b-136">xs:string</span></span>|<span data-ttu-id="8c01b-137">Identyfikator wystąpienia działania podrzędnego zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="8c01b-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="8c01b-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8c01b-138">AppDomain</span></span>|<span data-ttu-id="8c01b-139">xs:String</span><span class="sxs-lookup"><span data-stu-id="8c01b-139">xs:string</span></span>|<span data-ttu-id="8c01b-140">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8c01b-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

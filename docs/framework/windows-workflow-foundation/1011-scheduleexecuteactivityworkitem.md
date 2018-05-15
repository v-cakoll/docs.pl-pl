---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="dc54f-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="dc54f-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="dc54f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dc54f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc54f-104">ID</span><span class="sxs-lookup"><span data-stu-id="dc54f-104">ID</span></span>|<span data-ttu-id="dc54f-105">1011</span><span class="sxs-lookup"><span data-stu-id="dc54f-105">1011</span></span>|  
|<span data-ttu-id="dc54f-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="dc54f-106">Keywords</span></span>|<span data-ttu-id="dc54f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dc54f-107">WFRuntime</span></span>|  
|<span data-ttu-id="dc54f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="dc54f-108">Level</span></span>|<span data-ttu-id="dc54f-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="dc54f-109">Verbose</span></span>|  
|<span data-ttu-id="dc54f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="dc54f-110">Channel</span></span>|<span data-ttu-id="dc54f-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="dc54f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dc54f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dc54f-112">Description</span></span>  
 <span data-ttu-id="dc54f-113">Wskazuje, że zaplanowano element roboczy ExecuteActivityWorkItem.</span><span class="sxs-lookup"><span data-stu-id="dc54f-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dc54f-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="dc54f-114">Message</span></span>  
 <span data-ttu-id="dc54f-115">Zaplanowano element roboczy ExecuteActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="dc54f-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dc54f-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="dc54f-116">Details</span></span>  
  
|<span data-ttu-id="dc54f-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="dc54f-117">Data Item Name</span></span>|<span data-ttu-id="dc54f-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="dc54f-118">Data Item Type</span></span>|<span data-ttu-id="dc54f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="dc54f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dc54f-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="dc54f-120">Activity</span></span>|<span data-ttu-id="dc54f-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="dc54f-121">xs:string</span></span>|<span data-ttu-id="dc54f-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="dc54f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="dc54f-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="dc54f-123">DisplayName</span></span>|<span data-ttu-id="dc54f-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="dc54f-124">xs:string</span></span>|<span data-ttu-id="dc54f-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="dc54f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="dc54f-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="dc54f-126">InstanceId</span></span>|<span data-ttu-id="dc54f-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="dc54f-127">xs:string</span></span>|<span data-ttu-id="dc54f-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="dc54f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="dc54f-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="dc54f-129">AppDomain</span></span>|<span data-ttu-id="dc54f-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="dc54f-130">xs:string</span></span>|<span data-ttu-id="dc54f-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dc54f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

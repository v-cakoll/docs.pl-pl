---
title: 1011 — ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982257"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="467f3-102">1011 — ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="467f3-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="467f3-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="467f3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="467f3-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="467f3-104">ID</span></span>|<span data-ttu-id="467f3-105">1011</span><span class="sxs-lookup"><span data-stu-id="467f3-105">1011</span></span>|  
|<span data-ttu-id="467f3-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="467f3-106">Keywords</span></span>|<span data-ttu-id="467f3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="467f3-107">WFRuntime</span></span>|  
|<span data-ttu-id="467f3-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="467f3-108">Level</span></span>|<span data-ttu-id="467f3-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="467f3-109">Verbose</span></span>|  
|<span data-ttu-id="467f3-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="467f3-110">Channel</span></span>|<span data-ttu-id="467f3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="467f3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="467f3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="467f3-112">Description</span></span>  
 <span data-ttu-id="467f3-113">Wskazuje, że ExecuteActivityWorkItem została zaplanowana.</span><span class="sxs-lookup"><span data-stu-id="467f3-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="467f3-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="467f3-114">Message</span></span>  
 <span data-ttu-id="467f3-115">ExecuteActivityWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="467f3-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="467f3-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="467f3-116">Details</span></span>  
  
|<span data-ttu-id="467f3-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="467f3-117">Data Item Name</span></span>|<span data-ttu-id="467f3-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="467f3-118">Data Item Type</span></span>|<span data-ttu-id="467f3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="467f3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="467f3-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="467f3-120">Activity</span></span>|<span data-ttu-id="467f3-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="467f3-121">xs:string</span></span>|<span data-ttu-id="467f3-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="467f3-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="467f3-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="467f3-123">DisplayName</span></span>|<span data-ttu-id="467f3-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="467f3-124">xs:string</span></span>|<span data-ttu-id="467f3-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="467f3-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="467f3-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="467f3-126">InstanceId</span></span>|<span data-ttu-id="467f3-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="467f3-127">xs:string</span></span>|<span data-ttu-id="467f3-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="467f3-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="467f3-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="467f3-129">AppDomain</span></span>|<span data-ttu-id="467f3-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="467f3-130">xs:string</span></span>|<span data-ttu-id="467f3-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="467f3-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

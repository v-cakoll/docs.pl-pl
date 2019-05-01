---
title: 1032 — ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924868"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="c820a-102">1032 — ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="c820a-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c820a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c820a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c820a-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="c820a-104">ID</span></span>|<span data-ttu-id="c820a-105">1032</span><span class="sxs-lookup"><span data-stu-id="c820a-105">1032</span></span>|  
|<span data-ttu-id="c820a-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c820a-106">Keywords</span></span>|<span data-ttu-id="c820a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c820a-107">WFRuntime</span></span>|  
|<span data-ttu-id="c820a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c820a-108">Level</span></span>|<span data-ttu-id="c820a-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="c820a-109">Verbose</span></span>|  
|<span data-ttu-id="c820a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c820a-110">Channel</span></span>|<span data-ttu-id="c820a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c820a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c820a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c820a-112">Description</span></span>  
 <span data-ttu-id="c820a-113">Wskazuje, że RuntimeWorkItem została zaplanowana.</span><span class="sxs-lookup"><span data-stu-id="c820a-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c820a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c820a-114">Message</span></span>  
 <span data-ttu-id="c820a-115">Element roboczy środowiska uruchomieniowego została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="c820a-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c820a-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c820a-116">Details</span></span>  
  
|<span data-ttu-id="c820a-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c820a-117">Data Item Name</span></span>|<span data-ttu-id="c820a-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c820a-118">Data Item Type</span></span>|<span data-ttu-id="c820a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c820a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c820a-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="c820a-120">Activity</span></span>|<span data-ttu-id="c820a-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="c820a-121">xs:string</span></span>|<span data-ttu-id="c820a-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="c820a-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c820a-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="c820a-123">DisplayName</span></span>|<span data-ttu-id="c820a-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="c820a-124">xs:string</span></span>|<span data-ttu-id="c820a-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="c820a-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c820a-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c820a-126">InstanceId</span></span>|<span data-ttu-id="c820a-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="c820a-127">xs:string</span></span>|<span data-ttu-id="c820a-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="c820a-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c820a-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c820a-129">AppDomain</span></span>|<span data-ttu-id="c820a-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="c820a-130">xs:string</span></span>|<span data-ttu-id="c820a-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c820a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

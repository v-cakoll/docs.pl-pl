---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510250"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="31858-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="31858-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="31858-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="31858-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31858-104">ID</span><span class="sxs-lookup"><span data-stu-id="31858-104">ID</span></span>|<span data-ttu-id="31858-105">1032</span><span class="sxs-lookup"><span data-stu-id="31858-105">1032</span></span>|  
|<span data-ttu-id="31858-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="31858-106">Keywords</span></span>|<span data-ttu-id="31858-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="31858-107">WFRuntime</span></span>|  
|<span data-ttu-id="31858-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="31858-108">Level</span></span>|<span data-ttu-id="31858-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="31858-109">Verbose</span></span>|  
|<span data-ttu-id="31858-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="31858-110">Channel</span></span>|<span data-ttu-id="31858-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="31858-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31858-112">Opis</span><span class="sxs-lookup"><span data-stu-id="31858-112">Description</span></span>  
 <span data-ttu-id="31858-113">Wskazuje, że zaplanowano RuntimeWorkItem.</span><span class="sxs-lookup"><span data-stu-id="31858-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31858-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="31858-114">Message</span></span>  
 <span data-ttu-id="31858-115">Zaplanowano element roboczy środowiska wykonawczego dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="31858-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31858-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="31858-116">Details</span></span>  
  
|<span data-ttu-id="31858-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="31858-117">Data Item Name</span></span>|<span data-ttu-id="31858-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="31858-118">Data Item Type</span></span>|<span data-ttu-id="31858-119">Opis</span><span class="sxs-lookup"><span data-stu-id="31858-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31858-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="31858-120">Activity</span></span>|<span data-ttu-id="31858-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="31858-121">xs:string</span></span>|<span data-ttu-id="31858-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="31858-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="31858-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="31858-123">DisplayName</span></span>|<span data-ttu-id="31858-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="31858-124">xs:string</span></span>|<span data-ttu-id="31858-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="31858-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="31858-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="31858-126">InstanceId</span></span>|<span data-ttu-id="31858-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="31858-127">xs:string</span></span>|<span data-ttu-id="31858-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="31858-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="31858-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="31858-129">AppDomain</span></span>|<span data-ttu-id="31858-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="31858-130">xs:string</span></span>|<span data-ttu-id="31858-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="31858-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

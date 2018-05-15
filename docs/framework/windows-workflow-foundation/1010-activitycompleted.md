---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="01aa5-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="01aa5-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="01aa5-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="01aa5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01aa5-104">ID</span><span class="sxs-lookup"><span data-stu-id="01aa5-104">ID</span></span>|<span data-ttu-id="01aa5-105">1010</span><span class="sxs-lookup"><span data-stu-id="01aa5-105">1010</span></span>|  
|<span data-ttu-id="01aa5-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="01aa5-106">Keywords</span></span>|<span data-ttu-id="01aa5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="01aa5-107">WFRuntime</span></span>|  
|<span data-ttu-id="01aa5-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="01aa5-108">Level</span></span>|<span data-ttu-id="01aa5-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="01aa5-109">Information</span></span>|  
|<span data-ttu-id="01aa5-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="01aa5-110">Channel</span></span>|<span data-ttu-id="01aa5-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="01aa5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01aa5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="01aa5-112">Description</span></span>  
 <span data-ttu-id="01aa5-113">Wskazuje, że działanie zakończy działanie.</span><span class="sxs-lookup"><span data-stu-id="01aa5-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01aa5-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="01aa5-114">Message</span></span>  
 <span data-ttu-id="01aa5-115">Działanie "%1", nazwa wyświetlana: %2, identyfikator wystąpienia: '%3' została ukończona w stan "%4".</span><span class="sxs-lookup"><span data-stu-id="01aa5-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01aa5-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="01aa5-116">Details</span></span>  
  
|<span data-ttu-id="01aa5-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="01aa5-117">Data Item Name</span></span>|<span data-ttu-id="01aa5-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="01aa5-118">Data Item Type</span></span>|<span data-ttu-id="01aa5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="01aa5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01aa5-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="01aa5-120">Activity</span></span>|<span data-ttu-id="01aa5-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="01aa5-121">xs:string</span></span>|<span data-ttu-id="01aa5-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="01aa5-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="01aa5-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="01aa5-123">DisplayName</span></span>|<span data-ttu-id="01aa5-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="01aa5-124">xs:string</span></span>|<span data-ttu-id="01aa5-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="01aa5-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="01aa5-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="01aa5-126">InstanceId</span></span>|<span data-ttu-id="01aa5-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="01aa5-127">xs:string</span></span>|<span data-ttu-id="01aa5-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="01aa5-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="01aa5-129">Stan</span><span class="sxs-lookup"><span data-stu-id="01aa5-129">State</span></span>|<span data-ttu-id="01aa5-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="01aa5-130">xs:string</span></span>|<span data-ttu-id="01aa5-131">Stan działania.</span><span class="sxs-lookup"><span data-stu-id="01aa5-131">The state of the activity.</span></span>|  
|<span data-ttu-id="01aa5-132">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="01aa5-132">AppDomain</span></span>|<span data-ttu-id="01aa5-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="01aa5-133">xs:string</span></span>|<span data-ttu-id="01aa5-134">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="01aa5-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

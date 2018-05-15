---
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 28d19742055c51ca94c36ffddf15dced7dfc14cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="dff69-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="dff69-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="dff69-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dff69-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dff69-104">ID</span><span class="sxs-lookup"><span data-stu-id="dff69-104">ID</span></span>|<span data-ttu-id="dff69-105">1019</span><span class="sxs-lookup"><span data-stu-id="dff69-105">1019</span></span>|  
|<span data-ttu-id="dff69-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="dff69-106">Keywords</span></span>|<span data-ttu-id="dff69-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dff69-107">WFRuntime</span></span>|  
|<span data-ttu-id="dff69-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="dff69-108">Level</span></span>|<span data-ttu-id="dff69-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="dff69-109">Verbose</span></span>|  
|<span data-ttu-id="dff69-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="dff69-110">Channel</span></span>|<span data-ttu-id="dff69-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="dff69-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dff69-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dff69-112">Description</span></span>  
 <span data-ttu-id="dff69-113">Wskazuje, że element roboczy CancelActivityWorkItem została ukończona.</span><span class="sxs-lookup"><span data-stu-id="dff69-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dff69-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="dff69-114">Message</span></span>  
 <span data-ttu-id="dff69-115">Ukończono element roboczy CancelActivityWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="dff69-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dff69-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="dff69-116">Details</span></span>  
  
|<span data-ttu-id="dff69-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="dff69-117">Data Item Name</span></span>|<span data-ttu-id="dff69-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="dff69-118">Data Item Type</span></span>|<span data-ttu-id="dff69-119">Opis</span><span class="sxs-lookup"><span data-stu-id="dff69-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dff69-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="dff69-120">Activity</span></span>|<span data-ttu-id="dff69-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="dff69-121">xs:string</span></span>|<span data-ttu-id="dff69-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="dff69-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="dff69-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="dff69-123">DisplayName</span></span>|<span data-ttu-id="dff69-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="dff69-124">xs:string</span></span>|<span data-ttu-id="dff69-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="dff69-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="dff69-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="dff69-126">InstanceId</span></span>|<span data-ttu-id="dff69-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="dff69-127">xs:string</span></span>|<span data-ttu-id="dff69-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="dff69-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="dff69-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="dff69-129">AppDomain</span></span>|<span data-ttu-id="dff69-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="dff69-130">xs:string</span></span>|<span data-ttu-id="dff69-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dff69-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

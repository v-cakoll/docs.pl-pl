---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 6d0b43208f86c52e8863d4415a64466b0531832c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="d13ed-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="d13ed-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d13ed-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d13ed-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d13ed-104">ID</span><span class="sxs-lookup"><span data-stu-id="d13ed-104">ID</span></span>|<span data-ttu-id="d13ed-105">1026</span><span class="sxs-lookup"><span data-stu-id="d13ed-105">1026</span></span>|  
|<span data-ttu-id="d13ed-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d13ed-106">Keywords</span></span>|<span data-ttu-id="d13ed-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d13ed-107">WFRuntime</span></span>|  
|<span data-ttu-id="d13ed-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d13ed-108">Level</span></span>|<span data-ttu-id="d13ed-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="d13ed-109">Verbose</span></span>|  
|<span data-ttu-id="d13ed-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d13ed-110">Channel</span></span>|<span data-ttu-id="d13ed-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="d13ed-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d13ed-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d13ed-112">Description</span></span>  
 <span data-ttu-id="d13ed-113">Wskazuje, że zaplanowano element roboczy TransactionContextWorkItem.</span><span class="sxs-lookup"><span data-stu-id="d13ed-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d13ed-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d13ed-114">Message</span></span>  
 <span data-ttu-id="d13ed-115">Zaplanowano element roboczy TransactionContextWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d13ed-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d13ed-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d13ed-116">Details</span></span>  
  
|<span data-ttu-id="d13ed-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d13ed-117">Data Item Name</span></span>|<span data-ttu-id="d13ed-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d13ed-118">Data Item Type</span></span>|<span data-ttu-id="d13ed-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d13ed-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d13ed-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="d13ed-120">Activity</span></span>|<span data-ttu-id="d13ed-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="d13ed-121">xs:string</span></span>|<span data-ttu-id="d13ed-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="d13ed-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d13ed-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="d13ed-123">DisplayName</span></span>|<span data-ttu-id="d13ed-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="d13ed-124">xs:string</span></span>|<span data-ttu-id="d13ed-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="d13ed-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d13ed-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="d13ed-126">InstanceId</span></span>|<span data-ttu-id="d13ed-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="d13ed-127">xs:string</span></span>|<span data-ttu-id="d13ed-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="d13ed-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d13ed-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d13ed-129">AppDomain</span></span>|<span data-ttu-id="d13ed-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="d13ed-130">xs:string</span></span>|<span data-ttu-id="d13ed-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d13ed-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

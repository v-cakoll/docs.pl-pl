---
title: 1026 — ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 6d0b43208f86c52e8863d4415a64466b0531832c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924634"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="2b773-102">1026 — ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="2b773-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2b773-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2b773-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b773-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="2b773-104">ID</span></span>|<span data-ttu-id="2b773-105">1026</span><span class="sxs-lookup"><span data-stu-id="2b773-105">1026</span></span>|  
|<span data-ttu-id="2b773-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2b773-106">Keywords</span></span>|<span data-ttu-id="2b773-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2b773-107">WFRuntime</span></span>|  
|<span data-ttu-id="2b773-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2b773-108">Level</span></span>|<span data-ttu-id="2b773-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="2b773-109">Verbose</span></span>|  
|<span data-ttu-id="2b773-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2b773-110">Channel</span></span>|<span data-ttu-id="2b773-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2b773-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2b773-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2b773-112">Description</span></span>  
 <span data-ttu-id="2b773-113">Wskazuje, że TransactionContextWorkItem została zaplanowana.</span><span class="sxs-lookup"><span data-stu-id="2b773-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2b773-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2b773-114">Message</span></span>  
 <span data-ttu-id="2b773-115">TransactionContextWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="2b773-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2b773-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2b773-116">Details</span></span>  
  
|<span data-ttu-id="2b773-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2b773-117">Data Item Name</span></span>|<span data-ttu-id="2b773-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2b773-118">Data Item Type</span></span>|<span data-ttu-id="2b773-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2b773-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2b773-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="2b773-120">Activity</span></span>|<span data-ttu-id="2b773-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="2b773-121">xs:string</span></span>|<span data-ttu-id="2b773-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="2b773-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="2b773-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="2b773-123">DisplayName</span></span>|<span data-ttu-id="2b773-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="2b773-124">xs:string</span></span>|<span data-ttu-id="2b773-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="2b773-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="2b773-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="2b773-126">InstanceId</span></span>|<span data-ttu-id="2b773-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="2b773-127">xs:string</span></span>|<span data-ttu-id="2b773-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="2b773-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="2b773-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2b773-129">AppDomain</span></span>|<span data-ttu-id="2b773-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="2b773-130">xs:string</span></span>|<span data-ttu-id="2b773-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2b773-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

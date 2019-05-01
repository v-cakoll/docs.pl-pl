---
title: 1017 — ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 186b012cdd554ec7dd0d195b460619cca04eddcb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924491"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="909c8-102">1017 — ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="909c8-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="909c8-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="909c8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="909c8-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="909c8-104">ID</span></span>|<span data-ttu-id="909c8-105">1017</span><span class="sxs-lookup"><span data-stu-id="909c8-105">1017</span></span>|  
|<span data-ttu-id="909c8-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="909c8-106">Keywords</span></span>|<span data-ttu-id="909c8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="909c8-107">WFRuntime</span></span>|  
|<span data-ttu-id="909c8-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="909c8-108">Level</span></span>|<span data-ttu-id="909c8-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="909c8-109">Verbose</span></span>|  
|<span data-ttu-id="909c8-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="909c8-110">Channel</span></span>|<span data-ttu-id="909c8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="909c8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="909c8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="909c8-112">Description</span></span>  
 <span data-ttu-id="909c8-113">Wskazuje, że CancelActivityWorkItem została zaplanowana.</span><span class="sxs-lookup"><span data-stu-id="909c8-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="909c8-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="909c8-114">Message</span></span>  
 <span data-ttu-id="909c8-115">CancelActivityWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="909c8-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="909c8-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="909c8-116">Details</span></span>  
  
|<span data-ttu-id="909c8-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="909c8-117">Data Item Name</span></span>|<span data-ttu-id="909c8-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="909c8-118">Data Item Type</span></span>|<span data-ttu-id="909c8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="909c8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="909c8-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="909c8-120">Activity</span></span>|<span data-ttu-id="909c8-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="909c8-121">xs:string</span></span>|<span data-ttu-id="909c8-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="909c8-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="909c8-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="909c8-123">DisplayName</span></span>|<span data-ttu-id="909c8-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="909c8-124">xs:string</span></span>|<span data-ttu-id="909c8-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="909c8-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="909c8-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="909c8-126">InstanceId</span></span>|<span data-ttu-id="909c8-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="909c8-127">xs:string</span></span>|<span data-ttu-id="909c8-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="909c8-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="909c8-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="909c8-129">AppDomain</span></span>|<span data-ttu-id="909c8-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="909c8-130">xs:string</span></span>|<span data-ttu-id="909c8-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="909c8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

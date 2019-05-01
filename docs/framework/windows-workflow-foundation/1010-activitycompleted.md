---
title: 1010 — ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008374"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="db80b-102">1010 — ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="db80b-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="db80b-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="db80b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db80b-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="db80b-104">ID</span></span>|<span data-ttu-id="db80b-105">1010</span><span class="sxs-lookup"><span data-stu-id="db80b-105">1010</span></span>|  
|<span data-ttu-id="db80b-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="db80b-106">Keywords</span></span>|<span data-ttu-id="db80b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="db80b-107">WFRuntime</span></span>|  
|<span data-ttu-id="db80b-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="db80b-108">Level</span></span>|<span data-ttu-id="db80b-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="db80b-109">Information</span></span>|  
|<span data-ttu-id="db80b-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="db80b-110">Channel</span></span>|<span data-ttu-id="db80b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="db80b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db80b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="db80b-112">Description</span></span>  
 <span data-ttu-id="db80b-113">Wskazuje, że działanie zakończy działanie.</span><span class="sxs-lookup"><span data-stu-id="db80b-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="db80b-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="db80b-114">Message</span></span>  
 <span data-ttu-id="db80b-115">Działanie "%1", DisplayName: "%2", InstanceId: "%3" zostało ukończone w stanie "%4".</span><span class="sxs-lookup"><span data-stu-id="db80b-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="db80b-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="db80b-116">Details</span></span>  
  
|<span data-ttu-id="db80b-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="db80b-117">Data Item Name</span></span>|<span data-ttu-id="db80b-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="db80b-118">Data Item Type</span></span>|<span data-ttu-id="db80b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="db80b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="db80b-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="db80b-120">Activity</span></span>|<span data-ttu-id="db80b-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="db80b-121">xs:string</span></span>|<span data-ttu-id="db80b-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="db80b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="db80b-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="db80b-123">DisplayName</span></span>|<span data-ttu-id="db80b-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="db80b-124">xs:string</span></span>|<span data-ttu-id="db80b-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="db80b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="db80b-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="db80b-126">InstanceId</span></span>|<span data-ttu-id="db80b-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="db80b-127">xs:string</span></span>|<span data-ttu-id="db80b-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="db80b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="db80b-129">Stan</span><span class="sxs-lookup"><span data-stu-id="db80b-129">State</span></span>|<span data-ttu-id="db80b-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="db80b-130">xs:string</span></span>|<span data-ttu-id="db80b-131">Stan działania.</span><span class="sxs-lookup"><span data-stu-id="db80b-131">The state of the activity.</span></span>|  
|<span data-ttu-id="db80b-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="db80b-132">AppDomain</span></span>|<span data-ttu-id="db80b-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="db80b-133">xs:string</span></span>|<span data-ttu-id="db80b-134">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="db80b-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

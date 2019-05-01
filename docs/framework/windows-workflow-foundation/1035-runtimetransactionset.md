---
title: 1035 — RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924855"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="44cb5-102">1035 — RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="44cb5-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="44cb5-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="44cb5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44cb5-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="44cb5-104">ID</span></span>|<span data-ttu-id="44cb5-105">1035</span><span class="sxs-lookup"><span data-stu-id="44cb5-105">1035</span></span>|  
|<span data-ttu-id="44cb5-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="44cb5-106">Keywords</span></span>|<span data-ttu-id="44cb5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="44cb5-107">WFRuntime</span></span>|  
|<span data-ttu-id="44cb5-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="44cb5-108">Level</span></span>|<span data-ttu-id="44cb5-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="44cb5-109">Verbose</span></span>|  
|<span data-ttu-id="44cb5-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="44cb5-110">Channel</span></span>|<span data-ttu-id="44cb5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="44cb5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="44cb5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="44cb5-112">Description</span></span>  
 <span data-ttu-id="44cb5-113">Wskazuje, że działanie ustawił transakcji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="44cb5-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="44cb5-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="44cb5-114">Message</span></span>  
 <span data-ttu-id="44cb5-115">Transakcja środowiska uruchomieniowego została ustawiona przez działanie "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="44cb5-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="44cb5-116">Wykonanie wyizolowane do działania "%4", DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="44cb5-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="44cb5-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="44cb5-117">Details</span></span>  
  
|<span data-ttu-id="44cb5-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="44cb5-118">Data Item Name</span></span>|<span data-ttu-id="44cb5-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="44cb5-119">Data Item Type</span></span>|<span data-ttu-id="44cb5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="44cb5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="44cb5-121">Działanie</span><span class="sxs-lookup"><span data-stu-id="44cb5-121">Activity</span></span>|<span data-ttu-id="44cb5-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="44cb5-122">xs:string</span></span>|<span data-ttu-id="44cb5-123">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="44cb5-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="44cb5-124">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="44cb5-124">DisplayName</span></span>|<span data-ttu-id="44cb5-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="44cb5-125">xs:string</span></span>|<span data-ttu-id="44cb5-126">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="44cb5-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="44cb5-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="44cb5-127">InstanceId</span></span>|<span data-ttu-id="44cb5-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="44cb5-128">xs:string</span></span>|<span data-ttu-id="44cb5-129">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="44cb5-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="44cb5-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="44cb5-130">IsolatedActivity</span></span>|<span data-ttu-id="44cb5-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="44cb5-131">xs:string</span></span>|<span data-ttu-id="44cb5-132">Nazwa typu transakcji jest izolowane do działania.</span><span class="sxs-lookup"><span data-stu-id="44cb5-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="44cb5-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="44cb5-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="44cb5-134">xs:String</span><span class="sxs-lookup"><span data-stu-id="44cb5-134">xs:string</span></span>|<span data-ttu-id="44cb5-135">Nazwa wyświetlana transakcji jest izolowane do działania.</span><span class="sxs-lookup"><span data-stu-id="44cb5-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="44cb5-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="44cb5-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="44cb5-137">xs:String</span><span class="sxs-lookup"><span data-stu-id="44cb5-137">xs:string</span></span>|<span data-ttu-id="44cb5-138">Identyfikator wystąpienia transakcji jest izolowane do działania.</span><span class="sxs-lookup"><span data-stu-id="44cb5-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="44cb5-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="44cb5-139">AppDomain</span></span>|<span data-ttu-id="44cb5-140">xs:String</span><span class="sxs-lookup"><span data-stu-id="44cb5-140">xs:string</span></span>|<span data-ttu-id="44cb5-141">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="44cb5-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

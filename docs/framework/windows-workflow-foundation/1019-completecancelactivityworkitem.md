---
title: 1019 — CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 28d19742055c51ca94c36ffddf15dced7dfc14cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924439"
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="974ad-102">1019 — CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="974ad-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="974ad-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="974ad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="974ad-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="974ad-104">ID</span></span>|<span data-ttu-id="974ad-105">1019</span><span class="sxs-lookup"><span data-stu-id="974ad-105">1019</span></span>|  
|<span data-ttu-id="974ad-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="974ad-106">Keywords</span></span>|<span data-ttu-id="974ad-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="974ad-107">WFRuntime</span></span>|  
|<span data-ttu-id="974ad-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="974ad-108">Level</span></span>|<span data-ttu-id="974ad-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="974ad-109">Verbose</span></span>|  
|<span data-ttu-id="974ad-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="974ad-110">Channel</span></span>|<span data-ttu-id="974ad-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="974ad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="974ad-112">Opis</span><span class="sxs-lookup"><span data-stu-id="974ad-112">Description</span></span>  
 <span data-ttu-id="974ad-113">Wskazuje, że CancelActivityWorkItem zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="974ad-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="974ad-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="974ad-114">Message</span></span>  
 <span data-ttu-id="974ad-115">CancelActivityWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="974ad-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="974ad-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="974ad-116">Details</span></span>  
  
|<span data-ttu-id="974ad-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="974ad-117">Data Item Name</span></span>|<span data-ttu-id="974ad-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="974ad-118">Data Item Type</span></span>|<span data-ttu-id="974ad-119">Opis</span><span class="sxs-lookup"><span data-stu-id="974ad-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="974ad-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="974ad-120">Activity</span></span>|<span data-ttu-id="974ad-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="974ad-121">xs:string</span></span>|<span data-ttu-id="974ad-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="974ad-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="974ad-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="974ad-123">DisplayName</span></span>|<span data-ttu-id="974ad-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="974ad-124">xs:string</span></span>|<span data-ttu-id="974ad-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="974ad-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="974ad-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="974ad-126">InstanceId</span></span>|<span data-ttu-id="974ad-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="974ad-127">xs:string</span></span>|<span data-ttu-id="974ad-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="974ad-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="974ad-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="974ad-129">AppDomain</span></span>|<span data-ttu-id="974ad-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="974ad-130">xs:string</span></span>|<span data-ttu-id="974ad-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="974ad-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

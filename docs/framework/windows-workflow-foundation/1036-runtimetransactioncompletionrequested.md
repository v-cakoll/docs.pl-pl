---
title: 1036 — RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924842"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="bfd2d-102">1036 — RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="bfd2d-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="bfd2d-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="bfd2d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bfd2d-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="bfd2d-104">ID</span></span>|<span data-ttu-id="bfd2d-105">1036</span><span class="sxs-lookup"><span data-stu-id="bfd2d-105">1036</span></span>|  
|<span data-ttu-id="bfd2d-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="bfd2d-106">Keywords</span></span>|<span data-ttu-id="bfd2d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bfd2d-107">WFRuntime</span></span>|  
|<span data-ttu-id="bfd2d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="bfd2d-108">Level</span></span>|<span data-ttu-id="bfd2d-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="bfd2d-109">Verbose</span></span>|  
|<span data-ttu-id="bfd2d-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="bfd2d-110">Channel</span></span>|<span data-ttu-id="bfd2d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bfd2d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bfd2d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bfd2d-112">Description</span></span>  
 <span data-ttu-id="bfd2d-113">Wskazuje, że działanie zaplanowano ukończenia transakcji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bfd2d-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bfd2d-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="bfd2d-114">Message</span></span>  
 <span data-ttu-id="bfd2d-115">Działanie "%1", DisplayName: "%2", InstanceId: "%3" zaplanowano ukończenia transakcji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bfd2d-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bfd2d-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bfd2d-116">Details</span></span>  
  
|<span data-ttu-id="bfd2d-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="bfd2d-117">Data Item Name</span></span>|<span data-ttu-id="bfd2d-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="bfd2d-118">Data Item Type</span></span>|<span data-ttu-id="bfd2d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="bfd2d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bfd2d-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="bfd2d-120">Activity</span></span>|<span data-ttu-id="bfd2d-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="bfd2d-121">xs:string</span></span>|<span data-ttu-id="bfd2d-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="bfd2d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="bfd2d-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="bfd2d-123">DisplayName</span></span>|<span data-ttu-id="bfd2d-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="bfd2d-124">xs:string</span></span>|<span data-ttu-id="bfd2d-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="bfd2d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="bfd2d-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bfd2d-126">InstanceId</span></span>|<span data-ttu-id="bfd2d-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="bfd2d-127">xs:string</span></span>|<span data-ttu-id="bfd2d-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="bfd2d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bfd2d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bfd2d-129">AppDomain</span></span>|<span data-ttu-id="bfd2d-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="bfd2d-130">xs:string</span></span>|<span data-ttu-id="bfd2d-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bfd2d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

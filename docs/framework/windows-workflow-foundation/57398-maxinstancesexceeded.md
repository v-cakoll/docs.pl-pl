---
title: 57398 — MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945967"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="d6dd4-102">57398 — MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="d6dd4-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="d6dd4-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d6dd4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6dd4-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="d6dd4-104">ID</span></span>|<span data-ttu-id="d6dd4-105">57398</span><span class="sxs-lookup"><span data-stu-id="d6dd4-105">57398</span></span>|  
|<span data-ttu-id="d6dd4-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d6dd4-106">Keywords</span></span>|<span data-ttu-id="d6dd4-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="d6dd4-107">WFServices</span></span>|  
|<span data-ttu-id="d6dd4-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d6dd4-108">Level</span></span>|<span data-ttu-id="d6dd4-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="d6dd4-109">Warning</span></span>|  
|<span data-ttu-id="d6dd4-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d6dd4-110">Channel</span></span>|<span data-ttu-id="d6dd4-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d6dd4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d6dd4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d6dd4-112">Description</span></span>  
 <span data-ttu-id="d6dd4-113">Wskazuje, że system osiągnięty limit ustawiony dla ograniczenia "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="d6dd4-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d6dd4-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d6dd4-114">Message</span></span>  
 <span data-ttu-id="d6dd4-115">System osiągnięty limit ustawiony dla ograniczenia "MaxConcurrentInstances".</span><span class="sxs-lookup"><span data-stu-id="d6dd4-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="d6dd4-116">Limit dla tego ograniczania zostało ustawione na %1.</span><span class="sxs-lookup"><span data-stu-id="d6dd4-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="d6dd4-117">Wartość ograniczenia przepustowości można zmienić, modyfikując atrybut "maxConcurrentInstances" w elemencie serviceThrottle lub modyfikując właściwość "MaxConcurrentInstances" Zachowanie elementu ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="d6dd4-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d6dd4-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d6dd4-118">Details</span></span>  
  
|<span data-ttu-id="d6dd4-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d6dd4-119">Data Item Name</span></span>|<span data-ttu-id="d6dd4-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d6dd4-120">Data Item Type</span></span>|<span data-ttu-id="d6dd4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d6dd4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d6dd4-122">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d6dd4-122">Name</span></span>|<span data-ttu-id="d6dd4-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="d6dd4-123">xs:string</span></span>|<span data-ttu-id="d6dd4-124">Nazwa elementu.</span><span class="sxs-lookup"><span data-stu-id="d6dd4-124">The name of the item.</span></span>|  
|<span data-ttu-id="d6dd4-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d6dd4-125">AppDomain</span></span>|<span data-ttu-id="d6dd4-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="d6dd4-126">xs:string</span></span>|<span data-ttu-id="d6dd4-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d6dd4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

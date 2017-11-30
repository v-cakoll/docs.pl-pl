---
title: 225 - TraceCorrelationKeys
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a1f74ebfef7a2582f3eb25c3571cd05c4518ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="cd712-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="cd712-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="cd712-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cd712-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd712-104">ID</span><span class="sxs-lookup"><span data-stu-id="cd712-104">ID</span></span>|<span data-ttu-id="cd712-105">225</span><span class="sxs-lookup"><span data-stu-id="cd712-105">225</span></span>|  
|<span data-ttu-id="cd712-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cd712-106">Keywords</span></span>|<span data-ttu-id="cd712-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cd712-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="cd712-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="cd712-108">Level</span></span>|<span data-ttu-id="cd712-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="cd712-109">Information</span></span>|  
|<span data-ttu-id="cd712-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="cd712-110">Channel</span></span>|<span data-ttu-id="cd712-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="cd712-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cd712-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cd712-112">Description</span></span>  
 <span data-ttu-id="cd712-113">To zdarzenie jest emitowany stosowania korelacji na podstawie zawartości dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cd712-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="cd712-114">Zawiera klucze korelacji, które są stosowane do skorelowania komunikat do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cd712-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cd712-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="cd712-115">Message</span></span>  
 <span data-ttu-id="cd712-116">Oblicza klucz korelacji "%1" przy użyciu wartości "%2" w zakresie nadrzędnym "%3".</span><span class="sxs-lookup"><span data-stu-id="cd712-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cd712-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cd712-117">Details</span></span>  
  
|<span data-ttu-id="cd712-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="cd712-118">Data Item Name</span></span>|<span data-ttu-id="cd712-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="cd712-119">Data Item Type</span></span>|<span data-ttu-id="cd712-120">Opis</span><span class="sxs-lookup"><span data-stu-id="cd712-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cd712-121">Klucz wystąpienia</span><span class="sxs-lookup"><span data-stu-id="cd712-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="cd712-122">Klucz, który został wygenerowany na podstawie wartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="cd712-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="cd712-123">Wartości</span><span class="sxs-lookup"><span data-stu-id="cd712-123">Values</span></span>|`xs:string`|<span data-ttu-id="cd712-124">Wartości, które były używane do obliczania korelacji klucza wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cd712-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="cd712-125">Zakresu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="cd712-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="cd712-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="cd712-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="cd712-127">Dla usług sieci Web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cd712-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="cd712-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="cd712-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="cd712-129">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="cd712-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="cd712-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="cd712-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cd712-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cd712-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

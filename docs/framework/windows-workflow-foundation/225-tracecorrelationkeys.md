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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f4b6eb5df59977de91f1651a47a96cdf44bcf29
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="9db0c-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="9db0c-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="9db0c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9db0c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9db0c-104">ID</span><span class="sxs-lookup"><span data-stu-id="9db0c-104">ID</span></span>|<span data-ttu-id="9db0c-105">225</span><span class="sxs-lookup"><span data-stu-id="9db0c-105">225</span></span>|  
|<span data-ttu-id="9db0c-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="9db0c-106">Keywords</span></span>|<span data-ttu-id="9db0c-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9db0c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9db0c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="9db0c-108">Level</span></span>|<span data-ttu-id="9db0c-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="9db0c-109">Information</span></span>|  
|<span data-ttu-id="9db0c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="9db0c-110">Channel</span></span>|<span data-ttu-id="9db0c-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="9db0c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9db0c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9db0c-112">Description</span></span>  
 <span data-ttu-id="9db0c-113">To zdarzenie jest emitowany stosowania korelacji na podstawie zawartości dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9db0c-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="9db0c-114">Zawiera klucze korelacji, które są stosowane do skorelowania komunikat do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9db0c-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9db0c-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="9db0c-115">Message</span></span>  
 <span data-ttu-id="9db0c-116">Oblicza klucz korelacji "%1" przy użyciu wartości "%2" w zakresie nadrzędnym "%3".</span><span class="sxs-lookup"><span data-stu-id="9db0c-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9db0c-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9db0c-117">Details</span></span>  
  
|<span data-ttu-id="9db0c-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="9db0c-118">Data Item Name</span></span>|<span data-ttu-id="9db0c-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="9db0c-119">Data Item Type</span></span>|<span data-ttu-id="9db0c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9db0c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9db0c-121">Klucz wystąpienia</span><span class="sxs-lookup"><span data-stu-id="9db0c-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="9db0c-122">Klucz, który został wygenerowany na podstawie wartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="9db0c-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="9db0c-123">Wartości</span><span class="sxs-lookup"><span data-stu-id="9db0c-123">Values</span></span>|`xs:string`|<span data-ttu-id="9db0c-124">Wartości, które były używane do obliczania korelacji klucza wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9db0c-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="9db0c-125">Zakresu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="9db0c-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="9db0c-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="9db0c-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="9db0c-127">Dla usług sieci Web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9db0c-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9db0c-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="9db0c-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9db0c-129">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="9db0c-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9db0c-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="9db0c-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9db0c-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9db0c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

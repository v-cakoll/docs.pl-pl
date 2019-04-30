---
title: 225 — TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755665"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="660b2-102">225 — TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="660b2-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="660b2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="660b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="660b2-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="660b2-104">ID</span></span>|<span data-ttu-id="660b2-105">225</span><span class="sxs-lookup"><span data-stu-id="660b2-105">225</span></span>|  
|<span data-ttu-id="660b2-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="660b2-106">Keywords</span></span>|<span data-ttu-id="660b2-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="660b2-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="660b2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="660b2-108">Level</span></span>|<span data-ttu-id="660b2-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="660b2-109">Information</span></span>|  
|<span data-ttu-id="660b2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="660b2-110">Channel</span></span>|<span data-ttu-id="660b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="660b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="660b2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="660b2-112">Description</span></span>  
 <span data-ttu-id="660b2-113">To zdarzenie jest emitowane stosowania korelacji na podstawie zawartości dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="660b2-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="660b2-114">Zawiera on klucze korelacji, które są stosowane do korelowanie komunikatów na wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="660b2-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="660b2-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="660b2-115">Message</span></span>  
 <span data-ttu-id="660b2-116">Obliczona klucz korelacji "%1" przy użyciu wartości "%2" w zakresie nadrzędnym "%3".</span><span class="sxs-lookup"><span data-stu-id="660b2-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="660b2-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="660b2-117">Details</span></span>  
  
|<span data-ttu-id="660b2-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="660b2-118">Data Item Name</span></span>|<span data-ttu-id="660b2-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="660b2-119">Data Item Type</span></span>|<span data-ttu-id="660b2-120">Opis</span><span class="sxs-lookup"><span data-stu-id="660b2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="660b2-121">Klucz wystąpienia</span><span class="sxs-lookup"><span data-stu-id="660b2-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="660b2-122">Klucz, który został wygenerowany z wartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="660b2-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="660b2-123">Wartości</span><span class="sxs-lookup"><span data-stu-id="660b2-123">Values</span></span>|`xs:string`|<span data-ttu-id="660b2-124">Wartości, które były używane do obliczania klucza wystąpienia korelacji.</span><span class="sxs-lookup"><span data-stu-id="660b2-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="660b2-125">Zakresu nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="660b2-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="660b2-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="660b2-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="660b2-127">Dla usług sieci Web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="660b2-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="660b2-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="660b2-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="660b2-129">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="660b2-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="660b2-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="660b2-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="660b2-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="660b2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

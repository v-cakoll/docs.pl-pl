---
title: 203 — ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: 57192b44a0c3babc77fcca13ad4a1433b85bfdd7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781943"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="8183c-102">203 — ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="8183c-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="8183c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8183c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8183c-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8183c-104">ID</span></span>|<span data-ttu-id="8183c-105">203</span><span class="sxs-lookup"><span data-stu-id="8183c-105">203</span></span>|  
|<span data-ttu-id="8183c-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8183c-106">Keywords</span></span>|<span data-ttu-id="8183c-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8183c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8183c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8183c-108">Level</span></span>|<span data-ttu-id="8183c-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="8183c-109">Information</span></span>|  
|<span data-ttu-id="8183c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8183c-110">Channel</span></span>|<span data-ttu-id="8183c-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8183c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8183c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8183c-112">Description</span></span>  
 <span data-ttu-id="8183c-113">To zdarzenie jest emitowane po modelu usługi zostało wywołane `AfterCall` metody w Inspektorze parametru klienta.</span><span class="sxs-lookup"><span data-stu-id="8183c-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8183c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8183c-114">Message</span></span>  
 <span data-ttu-id="8183c-115">Dyspozytor wywoływane "AfterCall" na ClientParameterInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="8183c-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8183c-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8183c-116">Details</span></span>  
  
|<span data-ttu-id="8183c-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8183c-117">Data Item Name</span></span>|<span data-ttu-id="8183c-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8183c-118">Data Item Type</span></span>|<span data-ttu-id="8183c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8183c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8183c-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="8183c-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="8183c-121">Pełna nazwa CLR typu Inspektor wywołana.</span><span class="sxs-lookup"><span data-stu-id="8183c-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="8183c-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="8183c-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="8183c-123">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8183c-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8183c-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="8183c-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8183c-125">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="8183c-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8183c-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8183c-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8183c-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8183c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

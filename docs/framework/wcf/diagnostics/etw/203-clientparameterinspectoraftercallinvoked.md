---
title: 203 — ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: 57192b44a0c3babc77fcca13ad4a1433b85bfdd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458624"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="1f5c5-102">203 — ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="1f5c5-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="1f5c5-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1f5c5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1f5c5-104">ID</span><span class="sxs-lookup"><span data-stu-id="1f5c5-104">ID</span></span>|<span data-ttu-id="1f5c5-105">203</span><span class="sxs-lookup"><span data-stu-id="1f5c5-105">203</span></span>|  
|<span data-ttu-id="1f5c5-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1f5c5-106">Keywords</span></span>|<span data-ttu-id="1f5c5-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1f5c5-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1f5c5-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1f5c5-108">Level</span></span>|<span data-ttu-id="1f5c5-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="1f5c5-109">Information</span></span>|  
|<span data-ttu-id="1f5c5-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1f5c5-110">Channel</span></span>|<span data-ttu-id="1f5c5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1f5c5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1f5c5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1f5c5-112">Description</span></span>  
 <span data-ttu-id="1f5c5-113">To zdarzenie jest emitowany po modelu usługi został wywołany `AfterCall` metoda inspektora parametru klienta.</span><span class="sxs-lookup"><span data-stu-id="1f5c5-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1f5c5-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1f5c5-114">Message</span></span>  
 <span data-ttu-id="1f5c5-115">Dyspozytor wywołał metodę "AfterCall" w obiekcie ClientParameterInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="1f5c5-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1f5c5-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1f5c5-116">Details</span></span>  
  
|<span data-ttu-id="1f5c5-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1f5c5-117">Data Item Name</span></span>|<span data-ttu-id="1f5c5-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1f5c5-118">Data Item Type</span></span>|<span data-ttu-id="1f5c5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1f5c5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1f5c5-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="1f5c5-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="1f5c5-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="1f5c5-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="1f5c5-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="1f5c5-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="1f5c5-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1f5c5-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1f5c5-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="1f5c5-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1f5c5-125">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="1f5c5-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1f5c5-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1f5c5-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1f5c5-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1f5c5-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

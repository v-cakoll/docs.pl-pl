---
title: "212 — ParameterInspectorBeforeCallInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c428c9057e1538cfadb2b02bd05e2d61b4566399
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="2129b-102">212 — ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="2129b-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="2129b-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2129b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2129b-104">ID</span><span class="sxs-lookup"><span data-stu-id="2129b-104">ID</span></span>|<span data-ttu-id="2129b-105">212</span><span class="sxs-lookup"><span data-stu-id="2129b-105">212</span></span>|  
|<span data-ttu-id="2129b-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2129b-106">Keywords</span></span>|<span data-ttu-id="2129b-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2129b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2129b-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2129b-108">Level</span></span>|<span data-ttu-id="2129b-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="2129b-109">Information</span></span>|  
|<span data-ttu-id="2129b-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2129b-110">Channel</span></span>|<span data-ttu-id="2129b-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="2129b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2129b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2129b-112">Description</span></span>  
 <span data-ttu-id="2129b-113">To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeCall` metoda `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="2129b-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2129b-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2129b-114">Message</span></span>  
 <span data-ttu-id="2129b-115">Dyspozytor wywołał metodę "BeforeCall" w obiekcie ParameterInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="2129b-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2129b-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2129b-116">Details</span></span>  
  
|<span data-ttu-id="2129b-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2129b-117">Data Item Name</span></span>|<span data-ttu-id="2129b-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2129b-118">Data Item Type</span></span>|<span data-ttu-id="2129b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2129b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2129b-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="2129b-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="2129b-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="2129b-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="2129b-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="2129b-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="2129b-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2129b-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2129b-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="2129b-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2129b-125">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="2129b-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2129b-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="2129b-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2129b-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2129b-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

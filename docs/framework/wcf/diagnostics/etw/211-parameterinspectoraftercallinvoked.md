---
title: "211 — ParameterInspectorAfterCallInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69a9b6fe30a4ffa7f72e70b5aef740b2b772dd69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="cb317-102">211 — ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="cb317-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="cb317-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cb317-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb317-104">ID</span><span class="sxs-lookup"><span data-stu-id="cb317-104">ID</span></span>|<span data-ttu-id="cb317-105">211</span><span class="sxs-lookup"><span data-stu-id="cb317-105">211</span></span>|  
|<span data-ttu-id="cb317-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cb317-106">Keywords</span></span>|<span data-ttu-id="cb317-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cb317-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="cb317-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="cb317-108">Level</span></span>|<span data-ttu-id="cb317-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="cb317-109">Information</span></span>|  
|<span data-ttu-id="cb317-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="cb317-110">Channel</span></span>|<span data-ttu-id="cb317-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="cb317-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cb317-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cb317-112">Description</span></span>  
 <span data-ttu-id="cb317-113">To zdarzenie jest emitowany po modelu usługi został wywołany `AfterCall` metoda `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="cb317-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cb317-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="cb317-114">Message</span></span>  
 <span data-ttu-id="cb317-115">Dyspozytor wywołał metodę "AfterCall" w obiekcie ParameterInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="cb317-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cb317-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cb317-116">Details</span></span>  
  
|<span data-ttu-id="cb317-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="cb317-117">Data Item Name</span></span>|<span data-ttu-id="cb317-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="cb317-118">Data Item Type</span></span>|<span data-ttu-id="cb317-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cb317-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cb317-120">Nazwa typu</span><span class="sxs-lookup"><span data-stu-id="cb317-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="cb317-121">Imię i nazwisko CLR typu wywołanej `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="cb317-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="cb317-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="cb317-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="cb317-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cb317-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="cb317-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="cb317-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="cb317-125">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="cb317-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="cb317-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="cb317-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cb317-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cb317-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

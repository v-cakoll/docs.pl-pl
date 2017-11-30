---
title: "202 — ClientMessageInspectorBeforeSendInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: baf466bf63dcb9335a20eed8b563c222e09c7055
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="77ba8-102">202 — ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="77ba8-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="77ba8-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="77ba8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77ba8-104">ID</span><span class="sxs-lookup"><span data-stu-id="77ba8-104">ID</span></span>|<span data-ttu-id="77ba8-105">202</span><span class="sxs-lookup"><span data-stu-id="77ba8-105">202</span></span>|  
|<span data-ttu-id="77ba8-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="77ba8-106">Keywords</span></span>|<span data-ttu-id="77ba8-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="77ba8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="77ba8-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="77ba8-108">Level</span></span>|<span data-ttu-id="77ba8-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="77ba8-109">Information</span></span>|  
|<span data-ttu-id="77ba8-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="77ba8-110">Channel</span></span>|<span data-ttu-id="77ba8-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="77ba8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77ba8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="77ba8-112">Description</span></span>  
 <span data-ttu-id="77ba8-113">To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeSendRequest` metoda inspektora komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="77ba8-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77ba8-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="77ba8-114">Message</span></span>  
 <span data-ttu-id="77ba8-115">Dyspozytor wywołał "BeforeSendRequest" w obiekcie ClientMessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="77ba8-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77ba8-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="77ba8-116">Details</span></span>  
  
|<span data-ttu-id="77ba8-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="77ba8-117">Data Item Name</span></span>|<span data-ttu-id="77ba8-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="77ba8-118">Data Item Type</span></span>|<span data-ttu-id="77ba8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="77ba8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77ba8-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="77ba8-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="77ba8-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="77ba8-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="77ba8-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="77ba8-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="77ba8-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="77ba8-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="77ba8-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="77ba8-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="77ba8-125">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="77ba8-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="77ba8-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="77ba8-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="77ba8-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="77ba8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

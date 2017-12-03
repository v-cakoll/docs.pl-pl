---
title: "201 — ClientMessageInspectorAfterReceiveInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb6d243177700daa1e653c394e027a6f5428371
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="1ad01-102">201 — ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="1ad01-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="1ad01-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1ad01-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1ad01-104">ID</span><span class="sxs-lookup"><span data-stu-id="1ad01-104">ID</span></span>|<span data-ttu-id="1ad01-105">201</span><span class="sxs-lookup"><span data-stu-id="1ad01-105">201</span></span>|  
|<span data-ttu-id="1ad01-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1ad01-106">Keywords</span></span>|<span data-ttu-id="1ad01-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1ad01-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1ad01-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1ad01-108">Level</span></span>|<span data-ttu-id="1ad01-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="1ad01-109">Information</span></span>|  
|<span data-ttu-id="1ad01-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1ad01-110">Channel</span></span>|<span data-ttu-id="1ad01-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="1ad01-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1ad01-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad01-112">Description</span></span>  
 <span data-ttu-id="1ad01-113">To zdarzenie jest emitowany po modelu usługi został wywołany `AfterReceiveReply` metoda inspektora komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="1ad01-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1ad01-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1ad01-114">Message</span></span>  
 <span data-ttu-id="1ad01-115">Dyspozytor wywołał "AfterReceiveReply" w obiekcie ClientMessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="1ad01-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1ad01-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1ad01-116">Details</span></span>  
  
|<span data-ttu-id="1ad01-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1ad01-117">Data Item Name</span></span>|<span data-ttu-id="1ad01-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1ad01-118">Data Item Type</span></span>|<span data-ttu-id="1ad01-119">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad01-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1ad01-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="1ad01-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="1ad01-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="1ad01-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="1ad01-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="1ad01-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="1ad01-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1ad01-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1ad01-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="1ad01-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1ad01-125">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="1ad01-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1ad01-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1ad01-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1ad01-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1ad01-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: "209 — MessageInspectorBeforeSendInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9083a6dc9849fcd177b1e6a38ca7bb72e7799dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="4fb37-102">209 — MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="4fb37-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="4fb37-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4fb37-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4fb37-104">ID</span><span class="sxs-lookup"><span data-stu-id="4fb37-104">ID</span></span>|<span data-ttu-id="4fb37-105">209</span><span class="sxs-lookup"><span data-stu-id="4fb37-105">209</span></span>|  
|<span data-ttu-id="4fb37-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4fb37-106">Keywords</span></span>|<span data-ttu-id="4fb37-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4fb37-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4fb37-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="4fb37-108">Level</span></span>|<span data-ttu-id="4fb37-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="4fb37-109">Information</span></span>|  
|<span data-ttu-id="4fb37-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="4fb37-110">Channel</span></span>|<span data-ttu-id="4fb37-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="4fb37-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4fb37-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4fb37-112">Description</span></span>  
 <span data-ttu-id="4fb37-113">To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeSend` metoda inspektora wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4fb37-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4fb37-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="4fb37-114">Message</span></span>  
 <span data-ttu-id="4fb37-115">Dyspozytor wywołał "BeforeSendRequest" w obiekcie MessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="4fb37-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4fb37-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4fb37-116">Details</span></span>  
  
|<span data-ttu-id="4fb37-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="4fb37-117">Data Item Name</span></span>|<span data-ttu-id="4fb37-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="4fb37-118">Data Item Type</span></span>|<span data-ttu-id="4fb37-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4fb37-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4fb37-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="4fb37-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="4fb37-121">Imię i nazwisko CLR typu wywołanej `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="4fb37-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="4fb37-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="4fb37-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="4fb37-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4fb37-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4fb37-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="4fb37-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4fb37-125">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="4fb37-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4fb37-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="4fb37-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4fb37-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4fb37-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

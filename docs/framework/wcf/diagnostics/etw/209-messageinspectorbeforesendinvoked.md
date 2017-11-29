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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8de4338fd9d1d18ab1f689df39b2247a29d2dcf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="b34c6-102">209 — MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="b34c6-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="b34c6-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b34c6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b34c6-104">ID</span><span class="sxs-lookup"><span data-stu-id="b34c6-104">ID</span></span>|<span data-ttu-id="b34c6-105">209</span><span class="sxs-lookup"><span data-stu-id="b34c6-105">209</span></span>|  
|<span data-ttu-id="b34c6-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b34c6-106">Keywords</span></span>|<span data-ttu-id="b34c6-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b34c6-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b34c6-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b34c6-108">Level</span></span>|<span data-ttu-id="b34c6-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b34c6-109">Information</span></span>|  
|<span data-ttu-id="b34c6-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b34c6-110">Channel</span></span>|<span data-ttu-id="b34c6-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="b34c6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b34c6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b34c6-112">Description</span></span>  
 <span data-ttu-id="b34c6-113">To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeSend` metoda inspektora wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b34c6-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b34c6-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b34c6-114">Message</span></span>  
 <span data-ttu-id="b34c6-115">Dyspozytor wywołał "BeforeSendRequest" w obiekcie MessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="b34c6-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b34c6-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b34c6-116">Details</span></span>  
  
|<span data-ttu-id="b34c6-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b34c6-117">Data Item Name</span></span>|<span data-ttu-id="b34c6-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b34c6-118">Data Item Type</span></span>|<span data-ttu-id="b34c6-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b34c6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b34c6-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="b34c6-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="b34c6-121">Imię i nazwisko CLR typu wywołanej `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="b34c6-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="b34c6-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="b34c6-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="b34c6-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b34c6-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b34c6-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="b34c6-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b34c6-125">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="b34c6-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b34c6-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b34c6-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b34c6-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b34c6-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

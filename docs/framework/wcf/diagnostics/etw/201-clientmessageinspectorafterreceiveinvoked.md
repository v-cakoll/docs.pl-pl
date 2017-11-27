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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 907f4404e234ada2cf084f531a4de8fcfc84d6c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="8e829-102">201 — ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="8e829-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="8e829-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8e829-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e829-104">ID</span><span class="sxs-lookup"><span data-stu-id="8e829-104">ID</span></span>|<span data-ttu-id="8e829-105">201</span><span class="sxs-lookup"><span data-stu-id="8e829-105">201</span></span>|  
|<span data-ttu-id="8e829-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8e829-106">Keywords</span></span>|<span data-ttu-id="8e829-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8e829-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8e829-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8e829-108">Level</span></span>|<span data-ttu-id="8e829-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="8e829-109">Information</span></span>|  
|<span data-ttu-id="8e829-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8e829-110">Channel</span></span>|<span data-ttu-id="8e829-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="8e829-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8e829-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8e829-112">Description</span></span>  
 <span data-ttu-id="8e829-113">To zdarzenie jest emitowany po modelu usługi został wywołany `AfterReceiveReply` metoda inspektora komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="8e829-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8e829-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8e829-114">Message</span></span>  
 <span data-ttu-id="8e829-115">Dyspozytor wywołał "AfterReceiveReply" w obiekcie ClientMessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="8e829-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8e829-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8e829-116">Details</span></span>  
  
|<span data-ttu-id="8e829-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8e829-117">Data Item Name</span></span>|<span data-ttu-id="8e829-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8e829-118">Data Item Type</span></span>|<span data-ttu-id="8e829-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8e829-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8e829-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="8e829-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="8e829-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="8e829-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="8e829-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="8e829-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="8e829-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8e829-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8e829-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="8e829-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8e829-125">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="8e829-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8e829-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8e829-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8e829-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8e829-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

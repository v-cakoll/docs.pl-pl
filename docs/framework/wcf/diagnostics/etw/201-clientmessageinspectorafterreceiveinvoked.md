---
title: 201 — ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 96ca318c141d49e2ac5594d5ee101658a2aa8f21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="e44f6-102">201 — ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="e44f6-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="e44f6-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e44f6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e44f6-104">ID</span><span class="sxs-lookup"><span data-stu-id="e44f6-104">ID</span></span>|<span data-ttu-id="e44f6-105">201</span><span class="sxs-lookup"><span data-stu-id="e44f6-105">201</span></span>|  
|<span data-ttu-id="e44f6-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e44f6-106">Keywords</span></span>|<span data-ttu-id="e44f6-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e44f6-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e44f6-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e44f6-108">Level</span></span>|<span data-ttu-id="e44f6-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="e44f6-109">Information</span></span>|  
|<span data-ttu-id="e44f6-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e44f6-110">Channel</span></span>|<span data-ttu-id="e44f6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e44f6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e44f6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e44f6-112">Description</span></span>  
 <span data-ttu-id="e44f6-113">To zdarzenie jest emitowany po modelu usługi został wywołany `AfterReceiveReply` metoda inspektora komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="e44f6-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e44f6-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e44f6-114">Message</span></span>  
 <span data-ttu-id="e44f6-115">Dyspozytor wywołał "AfterReceiveReply" w obiekcie ClientMessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="e44f6-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e44f6-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e44f6-116">Details</span></span>  
  
|<span data-ttu-id="e44f6-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e44f6-117">Data Item Name</span></span>|<span data-ttu-id="e44f6-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e44f6-118">Data Item Type</span></span>|<span data-ttu-id="e44f6-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e44f6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e44f6-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="e44f6-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="e44f6-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="e44f6-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="e44f6-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="e44f6-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="e44f6-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e44f6-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e44f6-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="e44f6-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e44f6-125">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="e44f6-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e44f6-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e44f6-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e44f6-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e44f6-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

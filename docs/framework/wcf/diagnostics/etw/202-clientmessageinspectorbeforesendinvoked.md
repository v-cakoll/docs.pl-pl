---
title: 202 — ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 98de1d7e8e5e87ec7fbd783092f7fbc212fec65d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459358"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="b3a45-102">202 — ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="b3a45-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="b3a45-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b3a45-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b3a45-104">ID</span><span class="sxs-lookup"><span data-stu-id="b3a45-104">ID</span></span>|<span data-ttu-id="b3a45-105">202</span><span class="sxs-lookup"><span data-stu-id="b3a45-105">202</span></span>|  
|<span data-ttu-id="b3a45-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b3a45-106">Keywords</span></span>|<span data-ttu-id="b3a45-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b3a45-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b3a45-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b3a45-108">Level</span></span>|<span data-ttu-id="b3a45-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b3a45-109">Information</span></span>|  
|<span data-ttu-id="b3a45-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b3a45-110">Channel</span></span>|<span data-ttu-id="b3a45-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b3a45-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b3a45-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b3a45-112">Description</span></span>  
 <span data-ttu-id="b3a45-113">To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeSendRequest` metoda inspektora komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="b3a45-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b3a45-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b3a45-114">Message</span></span>  
 <span data-ttu-id="b3a45-115">Dyspozytor wywołał "BeforeSendRequest" w obiekcie ClientMessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="b3a45-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b3a45-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b3a45-116">Details</span></span>  
  
|<span data-ttu-id="b3a45-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b3a45-117">Data Item Name</span></span>|<span data-ttu-id="b3a45-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b3a45-118">Data Item Type</span></span>|<span data-ttu-id="b3a45-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b3a45-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b3a45-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="b3a45-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="b3a45-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="b3a45-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="b3a45-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="b3a45-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="b3a45-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b3a45-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b3a45-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="b3a45-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b3a45-125">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="b3a45-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b3a45-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b3a45-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b3a45-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b3a45-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

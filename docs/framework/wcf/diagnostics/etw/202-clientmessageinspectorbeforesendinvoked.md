---
title: 202 — ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 98de1d7e8e5e87ec7fbd783092f7fbc212fec65d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781995"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="8c118-102">202 — ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="8c118-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="8c118-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8c118-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c118-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="8c118-104">ID</span></span>|<span data-ttu-id="8c118-105">202</span><span class="sxs-lookup"><span data-stu-id="8c118-105">202</span></span>|  
|<span data-ttu-id="8c118-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8c118-106">Keywords</span></span>|<span data-ttu-id="8c118-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8c118-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8c118-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8c118-108">Level</span></span>|<span data-ttu-id="8c118-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="8c118-109">Information</span></span>|  
|<span data-ttu-id="8c118-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8c118-110">Channel</span></span>|<span data-ttu-id="8c118-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8c118-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c118-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8c118-112">Description</span></span>  
 <span data-ttu-id="8c118-113">To zdarzenie jest emitowane po modelu usługi zostało wywołane `BeforeSendRequest` metody w Inspektorze komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="8c118-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c118-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8c118-114">Message</span></span>  
 <span data-ttu-id="8c118-115">Dyspozytor wywoływane "BeforeSendRequest" na ClientMessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="8c118-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c118-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8c118-116">Details</span></span>  
  
|<span data-ttu-id="8c118-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8c118-117">Data Item Name</span></span>|<span data-ttu-id="8c118-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8c118-118">Data Item Type</span></span>|<span data-ttu-id="8c118-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8c118-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8c118-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="8c118-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="8c118-121">Pełna nazwa CLR typu Inspektor wywołana.</span><span class="sxs-lookup"><span data-stu-id="8c118-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="8c118-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="8c118-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="8c118-123">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8c118-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8c118-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="8c118-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8c118-125">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="8c118-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8c118-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8c118-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8c118-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8c118-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

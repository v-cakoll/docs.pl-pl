---
title: 201 — ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 96ca318c141d49e2ac5594d5ee101658a2aa8f21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782041"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="b4695-102">201 — ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="b4695-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="b4695-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b4695-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b4695-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="b4695-104">ID</span></span>|<span data-ttu-id="b4695-105">201</span><span class="sxs-lookup"><span data-stu-id="b4695-105">201</span></span>|  
|<span data-ttu-id="b4695-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b4695-106">Keywords</span></span>|<span data-ttu-id="b4695-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b4695-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b4695-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b4695-108">Level</span></span>|<span data-ttu-id="b4695-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b4695-109">Information</span></span>|  
|<span data-ttu-id="b4695-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b4695-110">Channel</span></span>|<span data-ttu-id="b4695-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b4695-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b4695-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b4695-112">Description</span></span>  
 <span data-ttu-id="b4695-113">To zdarzenie jest emitowane po modelu usługi zostało wywołane `AfterReceiveReply` metody w Inspektorze komunikat klienta.</span><span class="sxs-lookup"><span data-stu-id="b4695-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b4695-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b4695-114">Message</span></span>  
 <span data-ttu-id="b4695-115">Dyspozytor wywoływane "AfterReceiveReply" na ClientMessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="b4695-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b4695-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b4695-116">Details</span></span>  
  
|<span data-ttu-id="b4695-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b4695-117">Data Item Name</span></span>|<span data-ttu-id="b4695-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b4695-118">Data Item Type</span></span>|<span data-ttu-id="b4695-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b4695-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b4695-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="b4695-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="b4695-121">Pełna nazwa CLR typu Inspektor wywołana.</span><span class="sxs-lookup"><span data-stu-id="b4695-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="b4695-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="b4695-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="b4695-123">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b4695-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b4695-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="b4695-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b4695-125">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="b4695-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b4695-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b4695-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b4695-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b4695-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

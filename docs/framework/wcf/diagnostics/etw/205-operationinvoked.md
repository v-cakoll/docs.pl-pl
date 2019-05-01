---
title: 205 — OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781982"
---
# <a name="205---operationinvoked"></a><span data-ttu-id="2b07a-102">205 — OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="2b07a-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="2b07a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2b07a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b07a-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="2b07a-104">ID</span></span>|<span data-ttu-id="2b07a-105">205</span><span class="sxs-lookup"><span data-stu-id="2b07a-105">205</span></span>|  
|<span data-ttu-id="2b07a-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2b07a-106">Keywords</span></span>|<span data-ttu-id="2b07a-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2b07a-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2b07a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2b07a-108">Level</span></span>|<span data-ttu-id="2b07a-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="2b07a-109">Information</span></span>|  
|<span data-ttu-id="2b07a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2b07a-110">Channel</span></span>|<span data-ttu-id="2b07a-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2b07a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2b07a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2b07a-112">Description</span></span>  
 <span data-ttu-id="2b07a-113">To zdarzenie jest emitowane bezpośrednio przed domyślny Model usług `OperationInvoker` rozpoczyna się wywołanie do metody.</span><span class="sxs-lookup"><span data-stu-id="2b07a-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2b07a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2b07a-114">Message</span></span>  
 <span data-ttu-id="2b07a-115">OperationInvoker wywołał metodę "%1".</span><span class="sxs-lookup"><span data-stu-id="2b07a-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="2b07a-116">Informacje o wywołującym: "%2".</span><span class="sxs-lookup"><span data-stu-id="2b07a-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2b07a-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2b07a-117">Details</span></span>  
  
|<span data-ttu-id="2b07a-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2b07a-118">Data Item Name</span></span>|<span data-ttu-id="2b07a-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2b07a-119">Data Item Type</span></span>|<span data-ttu-id="2b07a-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2b07a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2b07a-121">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="2b07a-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="2b07a-122">Nazwa aparatu CLR metody, która została wywołana przez `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="2b07a-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="2b07a-123">Informacje o wywołującym</span><span class="sxs-lookup"><span data-stu-id="2b07a-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="2b07a-124">Adres IP i port numer klienta w formacie "IPAddress:PortNumber".</span><span class="sxs-lookup"><span data-stu-id="2b07a-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="2b07a-125">Te dwie wartości są pobierane z właściwości komunikatu "System.ServiceModel.Channels.RemoteEndpointMessageProperty" w kontekście operacji.</span><span class="sxs-lookup"><span data-stu-id="2b07a-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="2b07a-126">Należy pamiętać, że na inny niż TCP powiązania tej wartości `null`.</span><span class="sxs-lookup"><span data-stu-id="2b07a-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="2b07a-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="2b07a-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="2b07a-128">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2b07a-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2b07a-129">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="2b07a-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2b07a-130">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="2b07a-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2b07a-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2b07a-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2b07a-132">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2b07a-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

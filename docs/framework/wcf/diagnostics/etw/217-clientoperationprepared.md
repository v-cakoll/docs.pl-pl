---
title: 217 — ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781769"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="6dd7d-102">217 — ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="6dd7d-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="6dd7d-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6dd7d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6dd7d-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="6dd7d-104">ID</span></span>|<span data-ttu-id="6dd7d-105">217</span><span class="sxs-lookup"><span data-stu-id="6dd7d-105">217</span></span>|  
|<span data-ttu-id="6dd7d-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6dd7d-106">Keywords</span></span>|<span data-ttu-id="6dd7d-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6dd7d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6dd7d-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="6dd7d-108">Level</span></span>|<span data-ttu-id="6dd7d-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="6dd7d-109">Information</span></span>|  
|<span data-ttu-id="6dd7d-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="6dd7d-110">Channel</span></span>|<span data-ttu-id="6dd7d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6dd7d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6dd7d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6dd7d-112">Description</span></span>  
 <span data-ttu-id="6dd7d-113">To zdarzenie jest emitowane przez klientów przed operacją jest wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6dd7d-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="6dd7d-114">Message</span></span>  
 <span data-ttu-id="6dd7d-115">Klient jest wykonanie akcji "%1" skojarzonej z kontraktem "%2".</span><span class="sxs-lookup"><span data-stu-id="6dd7d-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="6dd7d-116">'% 3' zostanie wysłany komunikat.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6dd7d-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6dd7d-117">Details</span></span>  
  
|<span data-ttu-id="6dd7d-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="6dd7d-118">Data Item Name</span></span>|<span data-ttu-id="6dd7d-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="6dd7d-119">Data Item Type</span></span>|<span data-ttu-id="6dd7d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6dd7d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6dd7d-121">Akcja</span><span class="sxs-lookup"><span data-stu-id="6dd7d-121">Action</span></span>|`xs:string`|<span data-ttu-id="6dd7d-122">Nagłówek SOAP akcji w wiadomości wychodzących.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="6dd7d-123">Nazwa umowy</span><span class="sxs-lookup"><span data-stu-id="6dd7d-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="6dd7d-124">Nazwa kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-124">The name of the contract.</span></span> <span data-ttu-id="6dd7d-125">Przykład: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="6dd7d-126">Miejsce docelowe</span><span class="sxs-lookup"><span data-stu-id="6dd7d-126">Destination</span></span>|`xs:string`|<span data-ttu-id="6dd7d-127">Adres punktu końcowego usługi, który komunikat jest wysyłany do.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="6dd7d-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="6dd7d-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="6dd7d-129">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6dd7d-130">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="6dd7d-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6dd7d-131">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6dd7d-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6dd7d-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6dd7d-133">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

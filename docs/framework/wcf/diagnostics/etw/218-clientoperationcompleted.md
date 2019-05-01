---
title: 218 — ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781772"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="b8d09-102">218 — ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="b8d09-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="b8d09-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b8d09-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8d09-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="b8d09-104">ID</span></span>|<span data-ttu-id="b8d09-105">218</span><span class="sxs-lookup"><span data-stu-id="b8d09-105">218</span></span>|  
|<span data-ttu-id="b8d09-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b8d09-106">Keywords</span></span>|<span data-ttu-id="b8d09-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b8d09-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b8d09-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b8d09-108">Level</span></span>|<span data-ttu-id="b8d09-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b8d09-109">Information</span></span>|  
|<span data-ttu-id="b8d09-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b8d09-110">Channel</span></span>|<span data-ttu-id="b8d09-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b8d09-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b8d09-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b8d09-112">Description</span></span>  
 <span data-ttu-id="b8d09-113">To zdarzenie jest emitowane przez klientów, po prostu, po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="b8d09-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="b8d09-114">W przypadku operacji jednokierunkowych jest po pomyślnym wysłaniu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b8d09-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="b8d09-115">Dla operacji żądanie odpowiedź to po otrzymaniu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="b8d09-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b8d09-116">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b8d09-116">Message</span></span>  
 <span data-ttu-id="b8d09-117">Klient ukończyć wykonywania akcji "%1" skojarzonej z kontraktem "%2".</span><span class="sxs-lookup"><span data-stu-id="b8d09-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="b8d09-118">Wiadomość została wysłana do "%3".</span><span class="sxs-lookup"><span data-stu-id="b8d09-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b8d09-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b8d09-119">Details</span></span>  
  
|<span data-ttu-id="b8d09-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b8d09-120">Data Item Name</span></span>|<span data-ttu-id="b8d09-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b8d09-121">Data Item Type</span></span>|<span data-ttu-id="b8d09-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b8d09-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b8d09-123">Akcja</span><span class="sxs-lookup"><span data-stu-id="b8d09-123">Action</span></span>|<span data-ttu-id="b8d09-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="b8d09-124">xs:string</span></span>|<span data-ttu-id="b8d09-125">Nagłówek SOAP akcji w wiadomości wychodzących.</span><span class="sxs-lookup"><span data-stu-id="b8d09-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="b8d09-126">Nazwa umowy</span><span class="sxs-lookup"><span data-stu-id="b8d09-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="b8d09-127">Nazwa kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b8d09-127">The name of the contract.</span></span> <span data-ttu-id="b8d09-128">Przykład: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="b8d09-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="b8d09-129">Miejsce docelowe</span><span class="sxs-lookup"><span data-stu-id="b8d09-129">Destination</span></span>|`xs:string`|<span data-ttu-id="b8d09-130">Adres punktu końcowego usługi, z którego wysłano wiadomość.</span><span class="sxs-lookup"><span data-stu-id="b8d09-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="b8d09-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="b8d09-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="b8d09-132">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b8d09-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b8d09-133">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="b8d09-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b8d09-134">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="b8d09-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b8d09-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b8d09-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b8d09-136">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b8d09-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 218 — ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457977"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="04d50-102">218 — ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="04d50-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="04d50-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="04d50-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04d50-104">ID</span><span class="sxs-lookup"><span data-stu-id="04d50-104">ID</span></span>|<span data-ttu-id="04d50-105">218</span><span class="sxs-lookup"><span data-stu-id="04d50-105">218</span></span>|  
|<span data-ttu-id="04d50-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="04d50-106">Keywords</span></span>|<span data-ttu-id="04d50-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="04d50-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="04d50-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="04d50-108">Level</span></span>|<span data-ttu-id="04d50-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="04d50-109">Information</span></span>|  
|<span data-ttu-id="04d50-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="04d50-110">Channel</span></span>|<span data-ttu-id="04d50-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="04d50-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="04d50-112">Opis</span><span class="sxs-lookup"><span data-stu-id="04d50-112">Description</span></span>  
 <span data-ttu-id="04d50-113">To zdarzenie jest emitowane przez klientów zaraz po zakończeniu operacji.</span><span class="sxs-lookup"><span data-stu-id="04d50-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="04d50-114">W przypadku operacji jednokierunkowych jest tuż po wiadomość zostanie wysłana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="04d50-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="04d50-115">Dla operacji żądanie odpowiedź jest po odebraniu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="04d50-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="04d50-116">Komunikat</span><span class="sxs-lookup"><span data-stu-id="04d50-116">Message</span></span>  
 <span data-ttu-id="04d50-117">Klient ukończył wykonywanie akcji "%1" skojarzoną z kontraktem "%2".</span><span class="sxs-lookup"><span data-stu-id="04d50-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="04d50-118">Wiadomość została wysłana do "%3".</span><span class="sxs-lookup"><span data-stu-id="04d50-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="04d50-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="04d50-119">Details</span></span>  
  
|<span data-ttu-id="04d50-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="04d50-120">Data Item Name</span></span>|<span data-ttu-id="04d50-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="04d50-121">Data Item Type</span></span>|<span data-ttu-id="04d50-122">Opis</span><span class="sxs-lookup"><span data-stu-id="04d50-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="04d50-123">Akcja</span><span class="sxs-lookup"><span data-stu-id="04d50-123">Action</span></span>|<span data-ttu-id="04d50-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="04d50-124">xs:string</span></span>|<span data-ttu-id="04d50-125">Akcja SOAP nagłówka komunikatu wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="04d50-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="04d50-126">Nazwa umowy</span><span class="sxs-lookup"><span data-stu-id="04d50-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="04d50-127">Nazwa kontraktu.</span><span class="sxs-lookup"><span data-stu-id="04d50-127">The name of the contract.</span></span> <span data-ttu-id="04d50-128">Przykład: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="04d50-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="04d50-129">Miejsce docelowe</span><span class="sxs-lookup"><span data-stu-id="04d50-129">Destination</span></span>|`xs:string`|<span data-ttu-id="04d50-130">Adres punktu końcowego usługi, z którego wysłano wiadomość.</span><span class="sxs-lookup"><span data-stu-id="04d50-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="04d50-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="04d50-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="04d50-132">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="04d50-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="04d50-133">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="04d50-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="04d50-134">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="04d50-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="04d50-135">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="04d50-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="04d50-136">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="04d50-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

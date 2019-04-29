---
title: 301 — UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596482"
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="1986f-102">301 — UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="1986f-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="1986f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1986f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1986f-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="1986f-104">ID</span></span>|<span data-ttu-id="1986f-105">301</span><span class="sxs-lookup"><span data-stu-id="1986f-105">301</span></span>|  
|<span data-ttu-id="1986f-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1986f-106">Keywords</span></span>|<span data-ttu-id="1986f-107">Rozwiązywanie problemów, HealthMonitoring UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="1986f-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="1986f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1986f-108">Level</span></span>|<span data-ttu-id="1986f-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="1986f-109">Error</span></span>|  
|<span data-ttu-id="1986f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1986f-110">Channel</span></span>|<span data-ttu-id="1986f-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1986f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1986f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1986f-112">Description</span></span>  
 <span data-ttu-id="1986f-113">To zdarzenie jest emitowane przez kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1986f-113">This event is emitted from user code.</span></span> <span data-ttu-id="1986f-114">Deweloperzy może emitować to zdarzenie, gdy wystąpi błąd niestandardowy w ich usługi.</span><span class="sxs-lookup"><span data-stu-id="1986f-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="1986f-115">Można to zrobić za pomocą <xref:System.Diagnostics.Eventing> interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="1986f-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="1986f-116">Ponadto jest przykładowy WCF, otacza tego interfejsu API, który pokazuje, jak prawidłowo emisji to zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="1986f-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1986f-117">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1986f-117">Message</span></span>  
 <span data-ttu-id="1986f-118">Nazwa: "%1" dla odwołania: "%2", ładunek: %3</span><span class="sxs-lookup"><span data-stu-id="1986f-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="1986f-119">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1986f-119">Details</span></span>  
  
|<span data-ttu-id="1986f-120">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1986f-120">Data Item Name</span></span>|<span data-ttu-id="1986f-121">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1986f-121">Data Item Type</span></span>|<span data-ttu-id="1986f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1986f-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1986f-123">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1986f-123">Name</span></span>|`xs:string`|<span data-ttu-id="1986f-124">Zdefiniowana przez użytkownika nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1986f-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="1986f-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="1986f-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="1986f-126">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1986f-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1986f-127">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="1986f-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1986f-128">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="1986f-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1986f-129">ładunek</span><span class="sxs-lookup"><span data-stu-id="1986f-129">Payload</span></span>|`xs:string`|<span data-ttu-id="1986f-130">Zdefiniowane przez użytkownika ładunek zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1986f-130">The user-defined payload of the event.</span></span>|

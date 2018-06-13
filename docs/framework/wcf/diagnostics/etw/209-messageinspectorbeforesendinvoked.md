---
title: 209 — MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 24184c24b9affdf3a56d7968c02cf5354d690749
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458838"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="c231a-102">209 — MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="c231a-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="c231a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c231a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c231a-104">ID</span><span class="sxs-lookup"><span data-stu-id="c231a-104">ID</span></span>|<span data-ttu-id="c231a-105">209</span><span class="sxs-lookup"><span data-stu-id="c231a-105">209</span></span>|  
|<span data-ttu-id="c231a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c231a-106">Keywords</span></span>|<span data-ttu-id="c231a-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c231a-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c231a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c231a-108">Level</span></span>|<span data-ttu-id="c231a-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="c231a-109">Information</span></span>|  
|<span data-ttu-id="c231a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c231a-110">Channel</span></span>|<span data-ttu-id="c231a-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c231a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c231a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c231a-112">Description</span></span>  
 <span data-ttu-id="c231a-113">To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeSend` metoda inspektora wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c231a-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c231a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c231a-114">Message</span></span>  
 <span data-ttu-id="c231a-115">Dyspozytor wywołał "BeforeSendRequest" w obiekcie MessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="c231a-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c231a-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c231a-116">Details</span></span>  
  
|<span data-ttu-id="c231a-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c231a-117">Data Item Name</span></span>|<span data-ttu-id="c231a-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c231a-118">Data Item Type</span></span>|<span data-ttu-id="c231a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c231a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c231a-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="c231a-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="c231a-121">Imię i nazwisko CLR typu wywołanej `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="c231a-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="c231a-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="c231a-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="c231a-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c231a-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c231a-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c231a-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c231a-125">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c231a-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c231a-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c231a-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c231a-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c231a-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

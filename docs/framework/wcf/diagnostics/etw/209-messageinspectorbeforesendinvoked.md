---
title: 209 — MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 24184c24b9affdf3a56d7968c02cf5354d690749
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781886"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="32247-102">209 — MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="32247-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="32247-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="32247-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32247-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="32247-104">ID</span></span>|<span data-ttu-id="32247-105">209</span><span class="sxs-lookup"><span data-stu-id="32247-105">209</span></span>|  
|<span data-ttu-id="32247-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="32247-106">Keywords</span></span>|<span data-ttu-id="32247-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32247-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="32247-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="32247-108">Level</span></span>|<span data-ttu-id="32247-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="32247-109">Information</span></span>|  
|<span data-ttu-id="32247-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="32247-110">Channel</span></span>|<span data-ttu-id="32247-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="32247-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="32247-112">Opis</span><span class="sxs-lookup"><span data-stu-id="32247-112">Description</span></span>  
 <span data-ttu-id="32247-113">To zdarzenie jest emitowane po modelu usługi zostało wywołane `BeforeSend` metody w Inspektorze wiadomości.</span><span class="sxs-lookup"><span data-stu-id="32247-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="32247-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="32247-114">Message</span></span>  
 <span data-ttu-id="32247-115">Dyspozytor wywoływane "BeforeSendRequest" na MessageInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="32247-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="32247-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="32247-116">Details</span></span>  
  
|<span data-ttu-id="32247-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="32247-117">Data Item Name</span></span>|<span data-ttu-id="32247-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="32247-118">Data Item Type</span></span>|<span data-ttu-id="32247-119">Opis</span><span class="sxs-lookup"><span data-stu-id="32247-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="32247-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="32247-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="32247-121">Imię i nazwisko CLR typu wywołanej `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="32247-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="32247-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="32247-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="32247-123">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="32247-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="32247-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="32247-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="32247-125">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="32247-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="32247-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="32247-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="32247-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="32247-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

---
title: 204 — ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: eb060cfa79b75452deae67705126a24b7ca9ffef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782047"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="544aa-102">204 — ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="544aa-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="544aa-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="544aa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="544aa-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="544aa-104">ID</span></span>|<span data-ttu-id="544aa-105">204</span><span class="sxs-lookup"><span data-stu-id="544aa-105">204</span></span>|  
|<span data-ttu-id="544aa-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="544aa-106">Keywords</span></span>|<span data-ttu-id="544aa-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="544aa-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="544aa-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="544aa-108">Level</span></span>|<span data-ttu-id="544aa-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="544aa-109">Information</span></span>|  
|<span data-ttu-id="544aa-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="544aa-110">Channel</span></span>|<span data-ttu-id="544aa-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="544aa-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="544aa-112">Opis</span><span class="sxs-lookup"><span data-stu-id="544aa-112">Description</span></span>  
 <span data-ttu-id="544aa-113">To zdarzenie jest emitowane po modelu usługi zostało wywołane `BeforeCall` metody w Inspektorze parametru klienta.</span><span class="sxs-lookup"><span data-stu-id="544aa-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="544aa-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="544aa-114">Message</span></span>  
 <span data-ttu-id="544aa-115">Dyspozytor wywoływane "BeforeCall" na ClientParameterInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="544aa-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="544aa-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="544aa-116">Details</span></span>  
  
|<span data-ttu-id="544aa-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="544aa-117">Data Item Name</span></span>|<span data-ttu-id="544aa-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="544aa-118">Data Item Type</span></span>|<span data-ttu-id="544aa-119">Opis</span><span class="sxs-lookup"><span data-stu-id="544aa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="544aa-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="544aa-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="544aa-121">Pełna nazwa CLR typu Inspektor wywołana.</span><span class="sxs-lookup"><span data-stu-id="544aa-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="544aa-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="544aa-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="544aa-123">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="544aa-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="544aa-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="544aa-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="544aa-125">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="544aa-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="544aa-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="544aa-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="544aa-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="544aa-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

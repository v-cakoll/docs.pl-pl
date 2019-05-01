---
title: 212 — ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 02d4a4ed1e96983e132a1943dd39f9f885e5596a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781852"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="edf88-102">212 — ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="edf88-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="edf88-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="edf88-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="edf88-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="edf88-104">ID</span></span>|<span data-ttu-id="edf88-105">212</span><span class="sxs-lookup"><span data-stu-id="edf88-105">212</span></span>|  
|<span data-ttu-id="edf88-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="edf88-106">Keywords</span></span>|<span data-ttu-id="edf88-107">Rozwiązywanie problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="edf88-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="edf88-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="edf88-108">Level</span></span>|<span data-ttu-id="edf88-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="edf88-109">Information</span></span>|  
|<span data-ttu-id="edf88-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="edf88-110">Channel</span></span>|<span data-ttu-id="edf88-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="edf88-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="edf88-112">Opis</span><span class="sxs-lookup"><span data-stu-id="edf88-112">Description</span></span>  
 <span data-ttu-id="edf88-113">To zdarzenie jest emitowane po modelu usługi zostało wywołane `BeforeCall` metody `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="edf88-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="edf88-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="edf88-114">Message</span></span>  
 <span data-ttu-id="edf88-115">Dyspozytor wywoływane "BeforeCall" na ParameterInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="edf88-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="edf88-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="edf88-116">Details</span></span>  
  
|<span data-ttu-id="edf88-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="edf88-117">Data Item Name</span></span>|<span data-ttu-id="edf88-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="edf88-118">Data Item Type</span></span>|<span data-ttu-id="edf88-119">Opis</span><span class="sxs-lookup"><span data-stu-id="edf88-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="edf88-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="edf88-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="edf88-121">Pełna nazwa CLR typu Inspektor wywołana.</span><span class="sxs-lookup"><span data-stu-id="edf88-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="edf88-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="edf88-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="edf88-123">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="edf88-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="edf88-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="edf88-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="edf88-125">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="edf88-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="edf88-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="edf88-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="edf88-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="edf88-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

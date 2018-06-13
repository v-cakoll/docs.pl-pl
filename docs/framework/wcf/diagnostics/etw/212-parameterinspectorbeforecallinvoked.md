---
title: 212 — ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 02d4a4ed1e96983e132a1943dd39f9f885e5596a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458809"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="491fa-102">212 — ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="491fa-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="491fa-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="491fa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="491fa-104">ID</span><span class="sxs-lookup"><span data-stu-id="491fa-104">ID</span></span>|<span data-ttu-id="491fa-105">212</span><span class="sxs-lookup"><span data-stu-id="491fa-105">212</span></span>|  
|<span data-ttu-id="491fa-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="491fa-106">Keywords</span></span>|<span data-ttu-id="491fa-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="491fa-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="491fa-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="491fa-108">Level</span></span>|<span data-ttu-id="491fa-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="491fa-109">Information</span></span>|  
|<span data-ttu-id="491fa-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="491fa-110">Channel</span></span>|<span data-ttu-id="491fa-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="491fa-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="491fa-112">Opis</span><span class="sxs-lookup"><span data-stu-id="491fa-112">Description</span></span>  
 <span data-ttu-id="491fa-113">To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeCall` metoda `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="491fa-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="491fa-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="491fa-114">Message</span></span>  
 <span data-ttu-id="491fa-115">Dyspozytor wywołał metodę "BeforeCall" w obiekcie ParameterInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="491fa-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="491fa-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="491fa-116">Details</span></span>  
  
|<span data-ttu-id="491fa-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="491fa-117">Data Item Name</span></span>|<span data-ttu-id="491fa-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="491fa-118">Data Item Type</span></span>|<span data-ttu-id="491fa-119">Opis</span><span class="sxs-lookup"><span data-stu-id="491fa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="491fa-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="491fa-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="491fa-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="491fa-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="491fa-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="491fa-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="491fa-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="491fa-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="491fa-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="491fa-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="491fa-125">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="491fa-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="491fa-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="491fa-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="491fa-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="491fa-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

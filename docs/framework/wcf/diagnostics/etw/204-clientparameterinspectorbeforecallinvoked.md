---
title: 204 — ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: eb060cfa79b75452deae67705126a24b7ca9ffef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="be1ad-102">204 — ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="be1ad-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="be1ad-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="be1ad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be1ad-104">ID</span><span class="sxs-lookup"><span data-stu-id="be1ad-104">ID</span></span>|<span data-ttu-id="be1ad-105">204</span><span class="sxs-lookup"><span data-stu-id="be1ad-105">204</span></span>|  
|<span data-ttu-id="be1ad-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="be1ad-106">Keywords</span></span>|<span data-ttu-id="be1ad-107">Rozwiązywanie problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be1ad-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="be1ad-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="be1ad-108">Level</span></span>|<span data-ttu-id="be1ad-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="be1ad-109">Information</span></span>|  
|<span data-ttu-id="be1ad-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="be1ad-110">Channel</span></span>|<span data-ttu-id="be1ad-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="be1ad-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be1ad-112">Opis</span><span class="sxs-lookup"><span data-stu-id="be1ad-112">Description</span></span>  
 <span data-ttu-id="be1ad-113">To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeCall` metoda inspektora parametru klienta.</span><span class="sxs-lookup"><span data-stu-id="be1ad-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be1ad-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="be1ad-114">Message</span></span>  
 <span data-ttu-id="be1ad-115">Dyspozytor wywołał metodę "BeforeCall" w obiekcie ClientParameterInspector typu "%1".</span><span class="sxs-lookup"><span data-stu-id="be1ad-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="be1ad-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="be1ad-116">Details</span></span>  
  
|<span data-ttu-id="be1ad-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="be1ad-117">Data Item Name</span></span>|<span data-ttu-id="be1ad-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="be1ad-118">Data Item Type</span></span>|<span data-ttu-id="be1ad-119">Opis</span><span class="sxs-lookup"><span data-stu-id="be1ad-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be1ad-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="be1ad-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="be1ad-121">Element FullName CLR typu inspector wywołana.</span><span class="sxs-lookup"><span data-stu-id="be1ad-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="be1ad-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="be1ad-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="be1ad-123">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="be1ad-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="be1ad-124">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="be1ad-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="be1ad-125">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="be1ad-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="be1ad-126">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="be1ad-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="be1ad-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="be1ad-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

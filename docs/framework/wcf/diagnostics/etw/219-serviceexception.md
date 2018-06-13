---
title: 219 — ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460518"
---
# <a name="219---serviceexception"></a><span data-ttu-id="c3090-102">219 — ServiceException</span><span class="sxs-lookup"><span data-stu-id="c3090-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="c3090-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c3090-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3090-104">ID</span><span class="sxs-lookup"><span data-stu-id="c3090-104">ID</span></span>|<span data-ttu-id="c3090-105">219</span><span class="sxs-lookup"><span data-stu-id="c3090-105">219</span></span>|  
|<span data-ttu-id="c3090-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c3090-106">Keywords</span></span>|<span data-ttu-id="c3090-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c3090-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c3090-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c3090-108">Level</span></span>|<span data-ttu-id="c3090-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="c3090-109">Error</span></span>|  
|<span data-ttu-id="c3090-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c3090-110">Channel</span></span>|<span data-ttu-id="c3090-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c3090-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3090-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c3090-112">Description</span></span>  
 <span data-ttu-id="c3090-113">To zdarzenie jest emitowany, gdy usługa WCF napotka nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c3090-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="c3090-114">Dotyczy to również nieobsługiwanych wyjątków podczas aktywacji, podczas przetwarzania komunikatu i w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c3090-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3090-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c3090-115">Message</span></span>  
 <span data-ttu-id="c3090-116">Podczas przetwarzania komunikatu wystąpił nieobsługiwany wyjątek typu "%2".</span><span class="sxs-lookup"><span data-stu-id="c3090-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="c3090-117">ToString pełny wyjątek: %1.</span><span class="sxs-lookup"><span data-stu-id="c3090-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3090-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c3090-118">Details</span></span>  
  
|<span data-ttu-id="c3090-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c3090-119">Data Item Name</span></span>|<span data-ttu-id="c3090-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c3090-120">Data Item Type</span></span>|<span data-ttu-id="c3090-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c3090-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3090-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="c3090-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="c3090-123">Wyniku wywołania metody `ToString`() na wyjątku CLR.</span><span class="sxs-lookup"><span data-stu-id="c3090-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="c3090-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="c3090-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="c3090-125">Element FullName CLR typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c3090-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="c3090-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="c3090-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="c3090-127">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c3090-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c3090-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="c3090-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c3090-129">Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="c3090-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c3090-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c3090-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c3090-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c3090-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

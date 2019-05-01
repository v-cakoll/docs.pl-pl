---
title: 219 — ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781735"
---
# <a name="219---serviceexception"></a><span data-ttu-id="7ead1-102">219 — ServiceException</span><span class="sxs-lookup"><span data-stu-id="7ead1-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="7ead1-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7ead1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ead1-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="7ead1-104">ID</span></span>|<span data-ttu-id="7ead1-105">219</span><span class="sxs-lookup"><span data-stu-id="7ead1-105">219</span></span>|  
|<span data-ttu-id="7ead1-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7ead1-106">Keywords</span></span>|<span data-ttu-id="7ead1-107">EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7ead1-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7ead1-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7ead1-108">Level</span></span>|<span data-ttu-id="7ead1-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="7ead1-109">Error</span></span>|  
|<span data-ttu-id="7ead1-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7ead1-110">Channel</span></span>|<span data-ttu-id="7ead1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7ead1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7ead1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7ead1-112">Description</span></span>  
 <span data-ttu-id="7ead1-113">To zdarzenie jest emitowane, gdy usługa WCF napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7ead1-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="7ead1-114">Obejmuje to nieobsługiwane wyjątki podczas aktywacji, podczas przetwarzania komunikatu, a w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7ead1-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7ead1-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7ead1-115">Message</span></span>  
 <span data-ttu-id="7ead1-116">Wystąpił nieobsługiwany wyjątek typu "%2" podczas przetwarzania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7ead1-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="7ead1-117">ToString — pełny wyjątek: %1.</span><span class="sxs-lookup"><span data-stu-id="7ead1-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7ead1-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7ead1-118">Details</span></span>  
  
|<span data-ttu-id="7ead1-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7ead1-119">Data Item Name</span></span>|<span data-ttu-id="7ead1-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7ead1-120">Data Item Type</span></span>|<span data-ttu-id="7ead1-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7ead1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7ead1-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="7ead1-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="7ead1-123">Wynik wywołania metody `ToString`() na wyjątek CLR.</span><span class="sxs-lookup"><span data-stu-id="7ead1-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="7ead1-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="7ead1-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="7ead1-125">Pełna nazwa CLR typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7ead1-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="7ead1-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="7ead1-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="7ead1-127">W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7ead1-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7ead1-128">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="7ead1-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7ead1-129">Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="7ead1-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7ead1-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7ead1-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7ead1-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7ead1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|

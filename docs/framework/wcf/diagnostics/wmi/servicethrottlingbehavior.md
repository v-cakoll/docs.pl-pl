---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: edc154fcce0058455f1376a2a45807c92f7f2457
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190960"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="ab1fa-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="ab1fa-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="ab1fa-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="ab1fa-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab1fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab1fa-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ab1fa-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ab1fa-105">Methods</span></span>  
 <span data-ttu-id="ab1fa-106">Klasa elementu ServiceThrottlingBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="ab1fa-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab1fa-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ab1fa-107">Properties</span></span>  
 <span data-ttu-id="ab1fa-108">Klasa elementu ServiceThrottlingBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ab1fa-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="ab1fa-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="ab1fa-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="ab1fa-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="ab1fa-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="ab1fa-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ab1fa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab1fa-112">Maksymalna liczba komunikatów aktywnie przetwarzania dla wszystkich obiektów dyspozytora w elemencie ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="ab1fa-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="ab1fa-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="ab1fa-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="ab1fa-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="ab1fa-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ab1fa-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ab1fa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab1fa-116">Maksymalna liczba obiektów usługi, które mogą być wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="ab1fa-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="ab1fa-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="ab1fa-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="ab1fa-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="ab1fa-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="ab1fa-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ab1fa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab1fa-120">Maksymalna liczba sesji na hoście może akceptować w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="ab1fa-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab1fa-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab1fa-121">Requirements</span></span>  
  
|<span data-ttu-id="ab1fa-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="ab1fa-122">MOF</span></span>|<span data-ttu-id="ab1fa-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ab1fa-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ab1fa-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ab1fa-124">Namespace</span></span>|<span data-ttu-id="ab1fa-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ab1fa-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab1fa-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab1fa-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

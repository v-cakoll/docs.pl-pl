---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 98e8a720e92547ca0a893dd988b91cb7907660b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689854"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="c0237-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="c0237-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="c0237-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="c0237-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0237-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0237-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c0237-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c0237-105">Methods</span></span>  
 <span data-ttu-id="c0237-106">Klasa elementu ServiceThrottlingBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="c0237-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c0237-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c0237-107">Properties</span></span>  
 <span data-ttu-id="c0237-108">Klasa elementu ServiceThrottlingBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c0237-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="c0237-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="c0237-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="c0237-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="c0237-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="c0237-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c0237-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0237-112">Maksymalna liczba komunikatów aktywnie przetwarzania dla wszystkich obiektów dyspozytora w elemencie ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="c0237-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="c0237-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="c0237-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="c0237-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="c0237-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c0237-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c0237-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0237-116">Maksymalna liczba obiektów usługi, które mogą być wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="c0237-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="c0237-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="c0237-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="c0237-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="c0237-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c0237-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c0237-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0237-120">Maksymalna liczba sesji na hoście może akceptować w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="c0237-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0237-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0237-121">Requirements</span></span>  
  
|<span data-ttu-id="c0237-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c0237-122">MOF</span></span>|<span data-ttu-id="c0237-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c0237-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c0237-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c0237-124">Namespace</span></span>|<span data-ttu-id="c0237-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c0237-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0237-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0237-126">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

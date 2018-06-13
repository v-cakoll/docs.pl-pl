---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 9a7fbf93dbdbf1a6debcf865b4883b5784e2ff4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487610"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="2569f-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="2569f-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="2569f-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="2569f-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2569f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2569f-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2569f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2569f-105">Methods</span></span>  
 <span data-ttu-id="2569f-106">Klasy zachowania ServiceThrottlingBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="2569f-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2569f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2569f-107">Properties</span></span>  
 <span data-ttu-id="2569f-108">Klasy zachowania ServiceThrottlingBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="2569f-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="2569f-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="2569f-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="2569f-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="2569f-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="2569f-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2569f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2569f-112">Maksymalna liczba komunikatów aktywnie przetwarzanych w obrębie wszystkich obiektów dyspozytora w elemencie ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="2569f-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="2569f-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="2569f-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="2569f-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="2569f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="2569f-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2569f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2569f-116">Maksymalna liczba obiektów usługi, które mogą być wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="2569f-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="2569f-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="2569f-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="2569f-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="2569f-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="2569f-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2569f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2569f-120">Maksymalna liczba sesji, które host może zaakceptować jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="2569f-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2569f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2569f-121">Requirements</span></span>  
  
|<span data-ttu-id="2569f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="2569f-122">MOF</span></span>|<span data-ttu-id="2569f-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2569f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2569f-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="2569f-124">Namespace</span></span>|<span data-ttu-id="2569f-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2569f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2569f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2569f-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

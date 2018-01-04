---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccf1c167c4d1a072737f725de2fa0c132ca686f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="16ed2-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="16ed2-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="16ed2-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="16ed2-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16ed2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16ed2-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="16ed2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="16ed2-105">Methods</span></span>  
 <span data-ttu-id="16ed2-106">Klasy zachowania ServiceThrottlingBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="16ed2-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="16ed2-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="16ed2-107">Properties</span></span>  
 <span data-ttu-id="16ed2-108">Klasy zachowania ServiceThrottlingBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="16ed2-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="16ed2-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="16ed2-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="16ed2-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="16ed2-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="16ed2-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16ed2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16ed2-112">Maksymalna liczba komunikatów aktywnie przetwarzanych w obrębie wszystkich obiektów dyspozytora w elemencie ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="16ed2-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="16ed2-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="16ed2-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="16ed2-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="16ed2-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="16ed2-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16ed2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16ed2-116">Maksymalna liczba obiektów usługi, które mogą być wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="16ed2-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="16ed2-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="16ed2-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="16ed2-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="16ed2-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="16ed2-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="16ed2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16ed2-120">Maksymalna liczba sesji, które host może zaakceptować jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="16ed2-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16ed2-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16ed2-121">Requirements</span></span>  
  
|<span data-ttu-id="16ed2-122">MOF</span><span class="sxs-lookup"><span data-stu-id="16ed2-122">MOF</span></span>|<span data-ttu-id="16ed2-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="16ed2-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="16ed2-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="16ed2-124">Namespace</span></span>|<span data-ttu-id="16ed2-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="16ed2-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16ed2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16ed2-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

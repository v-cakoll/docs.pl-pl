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
ms.openlocfilehash: 59f85a148d6707876a4df512d5cfbd07ca0e54b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="afdf6-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="afdf6-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="afdf6-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="afdf6-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afdf6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afdf6-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="afdf6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="afdf6-105">Methods</span></span>  
 <span data-ttu-id="afdf6-106">Klasy zachowania ServiceThrottlingBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="afdf6-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="afdf6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="afdf6-107">Properties</span></span>  
 <span data-ttu-id="afdf6-108">Klasy zachowania ServiceThrottlingBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="afdf6-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="afdf6-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="afdf6-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="afdf6-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="afdf6-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="afdf6-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="afdf6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afdf6-112">Maksymalna liczba komunikatów aktywnie przetwarzanych w obrębie wszystkich obiektów dyspozytora w elemencie ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="afdf6-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="afdf6-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="afdf6-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="afdf6-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="afdf6-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="afdf6-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="afdf6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afdf6-116">Maksymalna liczba obiektów usługi, które mogą być wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="afdf6-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="afdf6-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="afdf6-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="afdf6-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="afdf6-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="afdf6-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="afdf6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afdf6-120">Maksymalna liczba sesji, które host może zaakceptować jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="afdf6-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afdf6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afdf6-121">Requirements</span></span>  
  
|<span data-ttu-id="afdf6-122">MOF</span><span class="sxs-lookup"><span data-stu-id="afdf6-122">MOF</span></span>|<span data-ttu-id="afdf6-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="afdf6-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="afdf6-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="afdf6-124">Namespace</span></span>|<span data-ttu-id="afdf6-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="afdf6-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afdf6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afdf6-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

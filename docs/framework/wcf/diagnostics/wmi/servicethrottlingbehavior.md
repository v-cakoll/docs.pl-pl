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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 779aabf5ec9b1bca7151eaf781c6dd6f2631b58f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="b509d-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="b509d-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="b509d-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="b509d-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b509d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b509d-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b509d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b509d-105">Methods</span></span>  
 <span data-ttu-id="b509d-106">Klasy zachowania ServiceThrottlingBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b509d-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b509d-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b509d-107">Properties</span></span>  
 <span data-ttu-id="b509d-108">Klasy zachowania ServiceThrottlingBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b509d-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="b509d-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="b509d-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="b509d-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b509d-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="b509d-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b509d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b509d-112">Maksymalna liczba komunikatów aktywnie przetwarzanych w obrębie wszystkich obiektów dyspozytora w elemencie ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="b509d-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="b509d-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="b509d-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="b509d-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b509d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b509d-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b509d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b509d-116">Maksymalna liczba obiektów usługi, które mogą być wykonywane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="b509d-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="b509d-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="b509d-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="b509d-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b509d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="b509d-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b509d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b509d-120">Maksymalna liczba sesji, które host może zaakceptować jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b509d-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b509d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b509d-121">Requirements</span></span>  
  
|<span data-ttu-id="b509d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b509d-122">MOF</span></span>|<span data-ttu-id="b509d-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b509d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b509d-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b509d-124">Namespace</span></span>|<span data-ttu-id="b509d-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b509d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b509d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b509d-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>

---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e297bfc0499ea3ee8d3dd8395165ca22b2baa1de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="59fec-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="59fec-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="59fec-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="59fec-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59fec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59fec-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="59fec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="59fec-105">Methods</span></span>  
 <span data-ttu-id="59fec-106">Element DeliveryRequirementsAttribute klasa nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="59fec-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="59fec-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="59fec-107">Properties</span></span>  
 <span data-ttu-id="59fec-108">Element DeliveryRequirementsAttribute klasa ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="59fec-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="59fec-109">Pola QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="59fec-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="59fec-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="59fec-110">Data type: string</span></span>  
  
 <span data-ttu-id="59fec-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="59fec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59fec-112">Określa, czy wiązanie dla usługi obsługuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="59fec-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="59fec-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="59fec-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="59fec-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="59fec-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="59fec-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="59fec-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59fec-116">Określa, czy wiązanie obsługuje uporządkowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="59fec-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="59fec-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="59fec-117">TargetContract</span></span>  
 <span data-ttu-id="59fec-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="59fec-118">Data type: string</span></span>  
  
 <span data-ttu-id="59fec-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="59fec-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59fec-120">Kontrakt, którego dotyczy.</span><span class="sxs-lookup"><span data-stu-id="59fec-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59fec-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59fec-121">Requirements</span></span>  
  
|<span data-ttu-id="59fec-122">MOF</span><span class="sxs-lookup"><span data-stu-id="59fec-122">MOF</span></span>|<span data-ttu-id="59fec-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="59fec-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="59fec-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="59fec-124">Namespace</span></span>|<span data-ttu-id="59fec-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="59fec-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59fec-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59fec-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

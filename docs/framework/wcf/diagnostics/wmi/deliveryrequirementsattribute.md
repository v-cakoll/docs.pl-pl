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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40bdc27337daae02795137fc3ac67575787018c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="5f8f9-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="5f8f9-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="5f8f9-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="5f8f9-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f8f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f8f9-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5f8f9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5f8f9-105">Methods</span></span>  
 <span data-ttu-id="5f8f9-106">Element DeliveryRequirementsAttribute klasa nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="5f8f9-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5f8f9-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5f8f9-107">Properties</span></span>  
 <span data-ttu-id="5f8f9-108">Element DeliveryRequirementsAttribute klasa ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="5f8f9-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="5f8f9-109">Pola QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="5f8f9-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="5f8f9-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="5f8f9-110">Data type: string</span></span>  
  
 <span data-ttu-id="5f8f9-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5f8f9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5f8f9-112">Określa, czy wiązanie dla usługi obsługuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="5f8f9-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="5f8f9-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="5f8f9-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="5f8f9-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="5f8f9-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="5f8f9-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5f8f9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5f8f9-116">Określa, czy wiązanie obsługuje uporządkowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="5f8f9-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="5f8f9-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="5f8f9-117">TargetContract</span></span>  
 <span data-ttu-id="5f8f9-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="5f8f9-118">Data type: string</span></span>  
  
 <span data-ttu-id="5f8f9-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5f8f9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5f8f9-120">Kontrakt, którego dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5f8f9-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f8f9-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f8f9-121">Requirements</span></span>  
  
|<span data-ttu-id="5f8f9-122">MOF</span><span class="sxs-lookup"><span data-stu-id="5f8f9-122">MOF</span></span>|<span data-ttu-id="5f8f9-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5f8f9-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5f8f9-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="5f8f9-124">Namespace</span></span>|<span data-ttu-id="5f8f9-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5f8f9-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f8f9-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f8f9-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

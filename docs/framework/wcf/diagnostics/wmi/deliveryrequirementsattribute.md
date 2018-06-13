---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: d294ba4f14472012b9e311ee53742633b5173f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485825"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="60130-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="60130-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="60130-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="60130-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60130-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60130-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="60130-105">Metody</span><span class="sxs-lookup"><span data-stu-id="60130-105">Methods</span></span>  
 <span data-ttu-id="60130-106">Element DeliveryRequirementsAttribute klasa nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="60130-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="60130-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="60130-107">Properties</span></span>  
 <span data-ttu-id="60130-108">Element DeliveryRequirementsAttribute klasa ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="60130-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="60130-109">Pola QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="60130-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="60130-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="60130-110">Data type: string</span></span>  
  
 <span data-ttu-id="60130-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="60130-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60130-112">Określa, czy wiązanie dla usługi obsługuje kontrakty.</span><span class="sxs-lookup"><span data-stu-id="60130-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="60130-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="60130-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="60130-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="60130-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="60130-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="60130-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60130-116">Określa, czy wiązanie obsługuje uporządkowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="60130-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="60130-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="60130-117">TargetContract</span></span>  
 <span data-ttu-id="60130-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="60130-118">Data type: string</span></span>  
  
 <span data-ttu-id="60130-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="60130-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60130-120">Kontrakt, którego dotyczy.</span><span class="sxs-lookup"><span data-stu-id="60130-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60130-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60130-121">Requirements</span></span>  
  
|<span data-ttu-id="60130-122">MOF</span><span class="sxs-lookup"><span data-stu-id="60130-122">MOF</span></span>|<span data-ttu-id="60130-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="60130-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="60130-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="60130-124">Namespace</span></span>|<span data-ttu-id="60130-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="60130-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60130-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60130-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

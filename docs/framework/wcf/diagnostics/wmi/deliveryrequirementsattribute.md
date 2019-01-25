---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 809e9d809bce456c831aab83c7ac19a882b2959b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571327"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="46dbd-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="46dbd-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="46dbd-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="46dbd-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46dbd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="46dbd-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="46dbd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="46dbd-105">Methods</span></span>  
 <span data-ttu-id="46dbd-106">Klasa Element DeliveryRequirementsAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="46dbd-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="46dbd-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="46dbd-107">Properties</span></span>  
 <span data-ttu-id="46dbd-108">Klasa Element DeliveryRequirementsAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="46dbd-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="46dbd-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="46dbd-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="46dbd-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="46dbd-110">Data type: string</span></span>  
  
 <span data-ttu-id="46dbd-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="46dbd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="46dbd-112">Określa, czy wiązanie dla usługi obsługuje umów.</span><span class="sxs-lookup"><span data-stu-id="46dbd-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="46dbd-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="46dbd-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="46dbd-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="46dbd-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="46dbd-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="46dbd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="46dbd-116">Określa, czy powiązanie obsługuje uporządkowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="46dbd-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="46dbd-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="46dbd-117">TargetContract</span></span>  
 <span data-ttu-id="46dbd-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="46dbd-118">Data type: string</span></span>  
  
 <span data-ttu-id="46dbd-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="46dbd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="46dbd-120">Kontrakt, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="46dbd-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46dbd-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46dbd-121">Requirements</span></span>  
  
|<span data-ttu-id="46dbd-122">MOF</span><span class="sxs-lookup"><span data-stu-id="46dbd-122">MOF</span></span>|<span data-ttu-id="46dbd-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="46dbd-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="46dbd-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="46dbd-124">Namespace</span></span>|<span data-ttu-id="46dbd-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="46dbd-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46dbd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46dbd-126">See also</span></span>
- <xref:System.ServiceModel.DeliveryRequirementsAttribute>

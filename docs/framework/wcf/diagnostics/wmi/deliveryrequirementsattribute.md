---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039679"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="7ef2d-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="7ef2d-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="7ef2d-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="7ef2d-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ef2d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ef2d-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7ef2d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7ef2d-105">Methods</span></span>  
 <span data-ttu-id="7ef2d-106">Klasa Element DeliveryRequirementsAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="7ef2d-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7ef2d-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7ef2d-107">Properties</span></span>  
 <span data-ttu-id="7ef2d-108">Klasa Element DeliveryRequirementsAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7ef2d-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="7ef2d-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="7ef2d-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="7ef2d-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="7ef2d-110">Data type: string</span></span>  
  
 <span data-ttu-id="7ef2d-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7ef2d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ef2d-112">Określa, czy wiązanie dla usługi obsługuje umów.</span><span class="sxs-lookup"><span data-stu-id="7ef2d-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="7ef2d-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="7ef2d-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="7ef2d-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="7ef2d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="7ef2d-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7ef2d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ef2d-116">Określa, czy powiązanie obsługuje uporządkowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="7ef2d-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="7ef2d-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="7ef2d-117">TargetContract</span></span>  
 <span data-ttu-id="7ef2d-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="7ef2d-118">Data type: string</span></span>  
  
 <span data-ttu-id="7ef2d-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7ef2d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ef2d-120">Kontrakt, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7ef2d-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ef2d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ef2d-121">Requirements</span></span>  
  
|<span data-ttu-id="7ef2d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7ef2d-122">MOF</span></span>|<span data-ttu-id="7ef2d-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7ef2d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7ef2d-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="7ef2d-124">Namespace</span></span>|<span data-ttu-id="7ef2d-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7ef2d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ef2d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ef2d-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>

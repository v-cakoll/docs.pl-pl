---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979215"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="069ad-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="069ad-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="069ad-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="069ad-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="069ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="069ad-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="069ad-105">Metody</span><span class="sxs-lookup"><span data-stu-id="069ad-105">Methods</span></span>  
 <span data-ttu-id="069ad-106">Klasa Element DeliveryRequirementsAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="069ad-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="069ad-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="069ad-107">Properties</span></span>  
 <span data-ttu-id="069ad-108">Klasa Element DeliveryRequirementsAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="069ad-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="069ad-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="069ad-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="069ad-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="069ad-110">Data type: string</span></span>  
  
 <span data-ttu-id="069ad-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="069ad-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="069ad-112">Określa, czy wiązanie dla usługi obsługuje umów.</span><span class="sxs-lookup"><span data-stu-id="069ad-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="069ad-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="069ad-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="069ad-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="069ad-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="069ad-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="069ad-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="069ad-116">Określa, czy powiązanie obsługuje uporządkowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="069ad-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="069ad-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="069ad-117">TargetContract</span></span>  
 <span data-ttu-id="069ad-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="069ad-118">Data type: string</span></span>  
  
 <span data-ttu-id="069ad-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="069ad-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="069ad-120">Kontrakt, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="069ad-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="069ad-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="069ad-121">Requirements</span></span>  
  
|<span data-ttu-id="069ad-122">MOF</span><span class="sxs-lookup"><span data-stu-id="069ad-122">MOF</span></span>|<span data-ttu-id="069ad-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="069ad-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="069ad-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="069ad-124">Namespace</span></span>|<span data-ttu-id="069ad-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="069ad-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="069ad-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="069ad-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>

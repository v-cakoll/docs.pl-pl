---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 7bfc03299fffc8070a7d8a4b3885706ea861bdf6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198517"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="def3a-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="def3a-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="def3a-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="def3a-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="def3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="def3a-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="def3a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="def3a-105">Methods</span></span>  
 <span data-ttu-id="def3a-106">Klasa Element DeliveryRequirementsAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="def3a-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="def3a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="def3a-107">Properties</span></span>  
 <span data-ttu-id="def3a-108">Klasa Element DeliveryRequirementsAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="def3a-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="def3a-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="def3a-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="def3a-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="def3a-110">Data type: string</span></span>  
  
 <span data-ttu-id="def3a-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="def3a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="def3a-112">Określa, czy wiązanie dla usługi obsługuje umów.</span><span class="sxs-lookup"><span data-stu-id="def3a-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="def3a-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="def3a-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="def3a-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="def3a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="def3a-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="def3a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="def3a-116">Określa, czy powiązanie obsługuje uporządkowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="def3a-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="def3a-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="def3a-117">TargetContract</span></span>  
 <span data-ttu-id="def3a-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="def3a-118">Data type: string</span></span>  
  
 <span data-ttu-id="def3a-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="def3a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="def3a-120">Kontrakt, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="def3a-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="def3a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="def3a-121">Requirements</span></span>  
  
|<span data-ttu-id="def3a-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="def3a-122">MOF</span></span>|<span data-ttu-id="def3a-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="def3a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="def3a-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="def3a-124">Namespace</span></span>|<span data-ttu-id="def3a-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="def3a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="def3a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="def3a-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

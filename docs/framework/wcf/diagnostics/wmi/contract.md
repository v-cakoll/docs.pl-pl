---
title: Kontrakt
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868434"
---
# <a name="contract"></a><span data-ttu-id="43c1d-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="43c1d-102">Contract</span></span>
<span data-ttu-id="43c1d-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="43c1d-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43c1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43c1d-104">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="43c1d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="43c1d-105">Methods</span></span>  
 <span data-ttu-id="43c1d-106">Klasa kontraktu nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="43c1d-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="43c1d-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="43c1d-107">Properties</span></span>  
 <span data-ttu-id="43c1d-108">Klasa kontraktu ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="43c1d-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="43c1d-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="43c1d-109">AppDomainId</span></span>  
 <span data-ttu-id="43c1d-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="43c1d-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="43c1d-111">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-112">Identyfikator domeny aplikacji, która hostuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="43c1d-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="43c1d-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="43c1d-113">Behaviors</span></span>  
 <span data-ttu-id="43c1d-114">Typ danych: Tablica zachowań</span><span class="sxs-lookup"><span data-stu-id="43c1d-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="43c1d-115">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-116">Zachowania skojarzone z tym kontraktem.</span><span class="sxs-lookup"><span data-stu-id="43c1d-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="43c1d-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="43c1d-117">Name</span></span>  
 <span data-ttu-id="43c1d-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="43c1d-118">Data type: string</span></span>  
  
 <span data-ttu-id="43c1d-119">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-120">Nazwa kontraktu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="43c1d-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="43c1d-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="43c1d-121">Namespace</span></span>  
 <span data-ttu-id="43c1d-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="43c1d-122">Data type: string</span></span>  
  
 <span data-ttu-id="43c1d-123">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-124">Przestrzeń nazw `portType` elementu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="43c1d-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="43c1d-125">Składowa</span><span class="sxs-lookup"><span data-stu-id="43c1d-125">Operations</span></span>  
 <span data-ttu-id="43c1d-126">Typ danych: Tablica operacji</span><span class="sxs-lookup"><span data-stu-id="43c1d-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="43c1d-127">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-128">Operacje na tym kontrakcie.</span><span class="sxs-lookup"><span data-stu-id="43c1d-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="43c1d-129">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="43c1d-129">ProcessId</span></span>  
 <span data-ttu-id="43c1d-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="43c1d-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="43c1d-131">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-132">Identyfikator procesu, który hostuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="43c1d-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="43c1d-133">ref</span><span class="sxs-lookup"><span data-stu-id="43c1d-133">ref</span></span>  
 <span data-ttu-id="43c1d-134">Typ danych: Kontrakt</span><span class="sxs-lookup"><span data-stu-id="43c1d-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="43c1d-135">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-136">Typ wywołania zwrotnego, gdy kontrakt jest kontraktem dwukierunkowym.</span><span class="sxs-lookup"><span data-stu-id="43c1d-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="43c1d-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="43c1d-137">SessionMode</span></span>  
 <span data-ttu-id="43c1d-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="43c1d-138">Data type: string</span></span>  
  
 <span data-ttu-id="43c1d-139">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-140">Wskazuje, czy kontrakt wymaga powiązania skojarzonego z tym kontraktem, aby można było używać sesji kanału.</span><span class="sxs-lookup"><span data-stu-id="43c1d-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="43c1d-141">Typ</span><span class="sxs-lookup"><span data-stu-id="43c1d-141">Type</span></span>  
 <span data-ttu-id="43c1d-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="43c1d-142">Data type: string</span></span>  
  
 <span data-ttu-id="43c1d-143">Typ dostępu: Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43c1d-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43c1d-144">Typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="43c1d-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43c1d-145">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43c1d-145">Requirements</span></span>  
  
|<span data-ttu-id="43c1d-146">PLIK</span><span class="sxs-lookup"><span data-stu-id="43c1d-146">MOF</span></span>|<span data-ttu-id="43c1d-147">Zadeklarowany w ServiceModel. mof.</span><span class="sxs-lookup"><span data-stu-id="43c1d-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="43c1d-148">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="43c1d-148">Namespace</span></span>|<span data-ttu-id="43c1d-149">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="43c1d-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43c1d-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43c1d-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>

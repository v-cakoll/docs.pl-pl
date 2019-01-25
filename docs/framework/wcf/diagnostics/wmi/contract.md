---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: c602ea2b708fced37c5b309596fe2312be21e741
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603567"
---
# <a name="contract"></a><span data-ttu-id="84520-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="84520-102">Contract</span></span>
<span data-ttu-id="84520-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="84520-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84520-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84520-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="84520-105">Metody</span><span class="sxs-lookup"><span data-stu-id="84520-105">Methods</span></span>  
 <span data-ttu-id="84520-106">Klasy kontraktu nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="84520-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="84520-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="84520-107">Properties</span></span>  
 <span data-ttu-id="84520-108">Klasa kontraktu ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="84520-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="84520-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="84520-109">AppDomainId</span></span>  
 <span data-ttu-id="84520-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="84520-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="84520-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-112">Identyfikator elementu appdomain umowy.</span><span class="sxs-lookup"><span data-stu-id="84520-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="84520-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="84520-113">Behaviors</span></span>  
 <span data-ttu-id="84520-114">Typ danych: Zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="84520-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="84520-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-116">Zachowania skojarzonego z nim.</span><span class="sxs-lookup"><span data-stu-id="84520-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="84520-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="84520-117">Name</span></span>  
 <span data-ttu-id="84520-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="84520-118">Data type: string</span></span>  
  
 <span data-ttu-id="84520-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-120">Nazwa kontraktu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="84520-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="84520-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="84520-121">Namespace</span></span>  
 <span data-ttu-id="84520-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="84520-122">Data type: string</span></span>  
  
 <span data-ttu-id="84520-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-124">Przestrzeń nazw `portType` elementu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="84520-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="84520-125">Operacje</span><span class="sxs-lookup"><span data-stu-id="84520-125">Operations</span></span>  
 <span data-ttu-id="84520-126">Typ danych: Operacja tablicy</span><span class="sxs-lookup"><span data-stu-id="84520-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="84520-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="84520-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="84520-129">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="84520-129">ProcessId</span></span>  
 <span data-ttu-id="84520-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="84520-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="84520-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-132">Proces identyfikator procesu, który obsługuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="84520-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="84520-133">ref</span><span class="sxs-lookup"><span data-stu-id="84520-133">ref</span></span>  
 <span data-ttu-id="84520-134">Typ danych: Kontrakt</span><span class="sxs-lookup"><span data-stu-id="84520-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="84520-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-136">Rodzaj wywołania zwrotnego, gdy kontrakt jest kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="84520-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="84520-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="84520-137">SessionMode</span></span>  
 <span data-ttu-id="84520-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="84520-138">Data type: string</span></span>  
  
 <span data-ttu-id="84520-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-140">Wskazuje, czy kontrakt wymaga powiązania skojarzonego z nim do użycia kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="84520-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="84520-141">Typ</span><span class="sxs-lookup"><span data-stu-id="84520-141">Type</span></span>  
 <span data-ttu-id="84520-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="84520-142">Data type: string</span></span>  
  
 <span data-ttu-id="84520-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="84520-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="84520-144">Typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="84520-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84520-145">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84520-145">Requirements</span></span>  
  
|<span data-ttu-id="84520-146">MOF</span><span class="sxs-lookup"><span data-stu-id="84520-146">MOF</span></span>|<span data-ttu-id="84520-147">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="84520-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="84520-148">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="84520-148">Namespace</span></span>|<span data-ttu-id="84520-149">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="84520-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84520-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84520-150">See also</span></span>
- <xref:System.ServiceModel.Description.ContractDescription>

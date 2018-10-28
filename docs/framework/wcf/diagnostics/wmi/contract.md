---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12e9cbf5232ebbad33ccc4fdca33233997d27357
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194673"
---
# <a name="contract"></a><span data-ttu-id="3af8f-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="3af8f-102">Contract</span></span>
<span data-ttu-id="3af8f-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="3af8f-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3af8f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="3af8f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3af8f-105">Methods</span></span>  
 <span data-ttu-id="3af8f-106">Klasy kontraktu nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="3af8f-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3af8f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3af8f-107">Properties</span></span>  
 <span data-ttu-id="3af8f-108">Klasa kontraktu ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3af8f-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="3af8f-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="3af8f-109">AppDomainId</span></span>  
 <span data-ttu-id="3af8f-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="3af8f-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="3af8f-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-112">Identyfikator elementu appdomain umowy.</span><span class="sxs-lookup"><span data-stu-id="3af8f-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="3af8f-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="3af8f-113">Behaviors</span></span>  
 <span data-ttu-id="3af8f-114">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="3af8f-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="3af8f-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-116">Zachowania skojarzonego z nim.</span><span class="sxs-lookup"><span data-stu-id="3af8f-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="3af8f-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3af8f-117">Name</span></span>  
 <span data-ttu-id="3af8f-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3af8f-118">Data type: string</span></span>  
  
 <span data-ttu-id="3af8f-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-120">Nazwa kontraktu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="3af8f-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="3af8f-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3af8f-121">Namespace</span></span>  
 <span data-ttu-id="3af8f-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3af8f-122">Data type: string</span></span>  
  
 <span data-ttu-id="3af8f-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-124">Przestrzeń nazw `portType` elementu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="3af8f-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="3af8f-125">Operacje</span><span class="sxs-lookup"><span data-stu-id="3af8f-125">Operations</span></span>  
 <span data-ttu-id="3af8f-126">Typ danych: operacja tablicy</span><span class="sxs-lookup"><span data-stu-id="3af8f-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="3af8f-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3af8f-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="3af8f-129">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="3af8f-129">ProcessId</span></span>  
 <span data-ttu-id="3af8f-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="3af8f-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="3af8f-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-132">Proces identyfikator procesu, który obsługuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="3af8f-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="3af8f-133">ref</span><span class="sxs-lookup"><span data-stu-id="3af8f-133">ref</span></span>  
 <span data-ttu-id="3af8f-134">Typ danych: kontraktu</span><span class="sxs-lookup"><span data-stu-id="3af8f-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="3af8f-135">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-136">Rodzaj wywołania zwrotnego, gdy kontrakt jest kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="3af8f-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="3af8f-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="3af8f-137">SessionMode</span></span>  
 <span data-ttu-id="3af8f-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3af8f-138">Data type: string</span></span>  
  
 <span data-ttu-id="3af8f-139">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-140">Wskazuje, czy kontrakt wymaga powiązania skojarzonego z nim do użycia kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="3af8f-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="3af8f-141">Typ</span><span class="sxs-lookup"><span data-stu-id="3af8f-141">Type</span></span>  
 <span data-ttu-id="3af8f-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3af8f-142">Data type: string</span></span>  
  
 <span data-ttu-id="3af8f-143">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3af8f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3af8f-144">Typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3af8f-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3af8f-145">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3af8f-145">Requirements</span></span>  
  
|<span data-ttu-id="3af8f-146">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="3af8f-146">MOF</span></span>|<span data-ttu-id="3af8f-147">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3af8f-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3af8f-148">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3af8f-148">Namespace</span></span>|<span data-ttu-id="3af8f-149">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3af8f-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3af8f-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3af8f-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>

---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 10789f9a2940c239ae20c8fd1e9d48bca0e820ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963699"
---
# <a name="contract"></a><span data-ttu-id="096f4-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="096f4-102">Contract</span></span>
<span data-ttu-id="096f4-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="096f4-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="096f4-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="096f4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="096f4-105">Methods</span></span>  
 <span data-ttu-id="096f4-106">Klasy kontraktu nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="096f4-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="096f4-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="096f4-107">Properties</span></span>  
 <span data-ttu-id="096f4-108">Klasa kontraktu ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="096f4-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="096f4-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="096f4-109">AppDomainId</span></span>  
 <span data-ttu-id="096f4-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="096f4-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="096f4-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-112">Identyfikator elementu appdomain umowy.</span><span class="sxs-lookup"><span data-stu-id="096f4-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="096f4-113">Zachowania</span><span class="sxs-lookup"><span data-stu-id="096f4-113">Behaviors</span></span>  
 <span data-ttu-id="096f4-114">Typ danych: Zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="096f4-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="096f4-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-116">Zachowania skojarzonego z nim.</span><span class="sxs-lookup"><span data-stu-id="096f4-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="096f4-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="096f4-117">Name</span></span>  
 <span data-ttu-id="096f4-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="096f4-118">Data type: string</span></span>  
  
 <span data-ttu-id="096f4-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-120">Nazwa kontraktu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="096f4-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="096f4-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="096f4-121">Namespace</span></span>  
 <span data-ttu-id="096f4-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="096f4-122">Data type: string</span></span>  
  
 <span data-ttu-id="096f4-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-124">Przestrzeń nazw `portType` elementu w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="096f4-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="096f4-125">Operacje</span><span class="sxs-lookup"><span data-stu-id="096f4-125">Operations</span></span>  
 <span data-ttu-id="096f4-126">Typ danych: Operacja tablicy</span><span class="sxs-lookup"><span data-stu-id="096f4-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="096f4-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="096f4-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="096f4-129">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="096f4-129">ProcessId</span></span>  
 <span data-ttu-id="096f4-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="096f4-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="096f4-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-132">Proces identyfikator procesu, który obsługuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="096f4-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="096f4-133">ref</span><span class="sxs-lookup"><span data-stu-id="096f4-133">ref</span></span>  
 <span data-ttu-id="096f4-134">Typ danych: Kontrakt</span><span class="sxs-lookup"><span data-stu-id="096f4-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="096f4-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-136">Rodzaj wywołania zwrotnego, gdy kontrakt jest kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="096f4-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="096f4-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="096f4-137">SessionMode</span></span>  
 <span data-ttu-id="096f4-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="096f4-138">Data type: string</span></span>  
  
 <span data-ttu-id="096f4-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-140">Wskazuje, czy kontrakt wymaga powiązania skojarzonego z nim do użycia kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="096f4-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="096f4-141">Typ</span><span class="sxs-lookup"><span data-stu-id="096f4-141">Type</span></span>  
 <span data-ttu-id="096f4-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="096f4-142">Data type: string</span></span>  
  
 <span data-ttu-id="096f4-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="096f4-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="096f4-144">Typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="096f4-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096f4-145">Wymagania</span><span class="sxs-lookup"><span data-stu-id="096f4-145">Requirements</span></span>  
  
|<span data-ttu-id="096f4-146">MOF</span><span class="sxs-lookup"><span data-stu-id="096f4-146">MOF</span></span>|<span data-ttu-id="096f4-147">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="096f4-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="096f4-148">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="096f4-148">Namespace</span></span>|<span data-ttu-id="096f4-149">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="096f4-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="096f4-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="096f4-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>

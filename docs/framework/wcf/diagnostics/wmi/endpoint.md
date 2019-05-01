---
title: Punkt końcowy
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 4562481e8b0b18c0ea0d9df0af3427ffe6419821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963608"
---
# <a name="endpoint"></a><span data-ttu-id="07af1-102">Punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="07af1-102">Endpoint</span></span>
<span data-ttu-id="07af1-103">Punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="07af1-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07af1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07af1-104">Syntax</span></span>  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="07af1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="07af1-105">Methods</span></span>  
 <span data-ttu-id="07af1-106">Klasa punktu końcowego definiuje następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="07af1-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="07af1-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="07af1-107">Method</span></span>|<span data-ttu-id="07af1-108">Opis</span><span class="sxs-lookup"><span data-stu-id="07af1-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07af1-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="07af1-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="07af1-110">Pobiera nazwę wystąpienia licznika wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="07af1-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="07af1-111">Właściwości</span><span class="sxs-lookup"><span data-stu-id="07af1-111">Properties</span></span>  
 <span data-ttu-id="07af1-112">Klasa punkt końcowy ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="07af1-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="07af1-113">Adres</span><span class="sxs-lookup"><span data-stu-id="07af1-113">Address</span></span>  
 <span data-ttu-id="07af1-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07af1-114">Data type: string</span></span>  
  
 <span data-ttu-id="07af1-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-116">Identyfikator URI, który zawiera adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="07af1-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="07af1-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="07af1-117">AddressHeaders</span></span>  
 <span data-ttu-id="07af1-118">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="07af1-118">Data type: string array</span></span>  
  
 <span data-ttu-id="07af1-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-120">Kolekcja nagłówków adresowych, dołączony do tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="07af1-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="07af1-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="07af1-121">AddressIdentity</span></span>  
 <span data-ttu-id="07af1-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07af1-122">Data type: string</span></span>  
  
 <span data-ttu-id="07af1-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-124">Tożsamość punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="07af1-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="07af1-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="07af1-125">AppDomainId</span></span>  
 <span data-ttu-id="07af1-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="07af1-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="07af1-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-128">Identyfikator elementu appdomain punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="07af1-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="07af1-129">Zachowania</span><span class="sxs-lookup"><span data-stu-id="07af1-129">Behaviors</span></span>  
 <span data-ttu-id="07af1-130">Typ danych: Zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="07af1-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="07af1-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-132">Kolekcja zachowań implementowanych przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="07af1-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="07af1-133">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="07af1-133">Binding</span></span>  
 <span data-ttu-id="07af1-134">Typ danych: Wiązanie</span><span class="sxs-lookup"><span data-stu-id="07af1-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="07af1-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-136">Wiązanie używane przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="07af1-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="07af1-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="07af1-137">ContractName</span></span>  
 <span data-ttu-id="07af1-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07af1-138">Data type: string</span></span>  
  
 <span data-ttu-id="07af1-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-140">Ciąg, który określa, który kontrakt tego punktu końcowego jest uwidaczniany.</span><span class="sxs-lookup"><span data-stu-id="07af1-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="07af1-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="07af1-141">CounterInstanceName</span></span>  
 <span data-ttu-id="07af1-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07af1-142">Data type: string</span></span>  
  
 <span data-ttu-id="07af1-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-144">Nazwa wystąpienia liczników wydajności punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="07af1-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="07af1-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="07af1-145">ListenUri</span></span>  
 <span data-ttu-id="07af1-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07af1-146">Data type: string</span></span>  
  
 <span data-ttu-id="07af1-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-148">Identyfikator Uri punktu końcowego nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="07af1-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="07af1-149">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07af1-149">Name</span></span>  
 <span data-ttu-id="07af1-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07af1-150">Data type: string</span></span>  
  
 <span data-ttu-id="07af1-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-152">Unikatowa nazwa tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="07af1-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="07af1-153">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="07af1-153">ProcessId</span></span>  
 <span data-ttu-id="07af1-154">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="07af1-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="07af1-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-156">Proces identyfikator procesu, który jest hostem punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="07af1-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="07af1-157">ref</span><span class="sxs-lookup"><span data-stu-id="07af1-157">ref</span></span>  
 <span data-ttu-id="07af1-158">Typ danych: Kontrakt</span><span class="sxs-lookup"><span data-stu-id="07af1-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="07af1-159">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07af1-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07af1-160">Kontrakt tego punktu końcowego jest uwidaczniany.</span><span class="sxs-lookup"><span data-stu-id="07af1-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07af1-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07af1-161">Requirements</span></span>  
  
|<span data-ttu-id="07af1-162">MOF</span><span class="sxs-lookup"><span data-stu-id="07af1-162">MOF</span></span>|<span data-ttu-id="07af1-163">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="07af1-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="07af1-164">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="07af1-164">Namespace</span></span>|<span data-ttu-id="07af1-165">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="07af1-165">Defined in root\ServiceModel</span></span>|

---
title: Punkt końcowy
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 5d597e9e029cec3552c94b47a64dfbf36d933e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint"></a><span data-ttu-id="6d716-102">Punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="6d716-102">Endpoint</span></span>
<span data-ttu-id="6d716-103">Punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="6d716-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d716-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d716-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="6d716-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6d716-105">Methods</span></span>  
 <span data-ttu-id="6d716-106">Klasa punktu końcowego definiuje następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="6d716-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="6d716-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="6d716-107">Method</span></span>|<span data-ttu-id="6d716-108">Opis</span><span class="sxs-lookup"><span data-stu-id="6d716-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d716-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="6d716-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="6d716-110">Pobiera nazwę wystąpienia licznika wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="6d716-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="6d716-111">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6d716-111">Properties</span></span>  
 <span data-ttu-id="6d716-112">Klasa punkt końcowy ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="6d716-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="6d716-113">Adres</span><span class="sxs-lookup"><span data-stu-id="6d716-113">Address</span></span>  
 <span data-ttu-id="6d716-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6d716-114">Data type: string</span></span>  
  
 <span data-ttu-id="6d716-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-116">Identyfikator URI zawierający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6d716-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="6d716-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="6d716-117">AddressHeaders</span></span>  
 <span data-ttu-id="6d716-118">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="6d716-118">Data type: string array</span></span>  
  
 <span data-ttu-id="6d716-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-120">Kolekcja nagłówków adresu przyłączonych do tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6d716-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="6d716-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="6d716-121">AddressIdentity</span></span>  
 <span data-ttu-id="6d716-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6d716-122">Data type: string</span></span>  
  
 <span data-ttu-id="6d716-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-124">Tożsamość punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6d716-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="6d716-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="6d716-125">AppDomainId</span></span>  
 <span data-ttu-id="6d716-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="6d716-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="6d716-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-128">Identyfikator domeny aplikacji obsługującej punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="6d716-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="6d716-129">Zachowania</span><span class="sxs-lookup"><span data-stu-id="6d716-129">Behaviors</span></span>  
 <span data-ttu-id="6d716-130">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="6d716-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="6d716-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-132">Kolekcja zachowań implementowanych przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="6d716-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="6d716-133">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="6d716-133">Binding</span></span>  
 <span data-ttu-id="6d716-134">Typ danych: powiązanie</span><span class="sxs-lookup"><span data-stu-id="6d716-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="6d716-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-136">Powiązanie używane przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="6d716-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="6d716-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="6d716-137">ContractName</span></span>  
 <span data-ttu-id="6d716-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6d716-138">Data type: string</span></span>  
  
 <span data-ttu-id="6d716-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-140">Ciąg określający, który kontrakt jest ujawniany ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="6d716-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="6d716-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="6d716-141">CounterInstanceName</span></span>  
 <span data-ttu-id="6d716-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6d716-142">Data type: string</span></span>  
  
 <span data-ttu-id="6d716-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-144">Nazwa wystąpienia liczników wydajności punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6d716-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="6d716-145">Identyfikator ListenUri</span><span class="sxs-lookup"><span data-stu-id="6d716-145">ListenUri</span></span>  
 <span data-ttu-id="6d716-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6d716-146">Data type: string</span></span>  
  
 <span data-ttu-id="6d716-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-148">Identyfikator Uri punktu końcowego nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="6d716-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="6d716-149">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6d716-149">Name</span></span>  
 <span data-ttu-id="6d716-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6d716-150">Data type: string</span></span>  
  
 <span data-ttu-id="6d716-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-152">Unikatowa nazwa tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="6d716-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="6d716-153">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="6d716-153">ProcessId</span></span>  
 <span data-ttu-id="6d716-154">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="6d716-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="6d716-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-156">Identyfikator procesu obsługującego punkt końcowy procesu.</span><span class="sxs-lookup"><span data-stu-id="6d716-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="6d716-157">ref</span><span class="sxs-lookup"><span data-stu-id="6d716-157">ref</span></span>  
 <span data-ttu-id="6d716-158">Typ danych: kontraktu</span><span class="sxs-lookup"><span data-stu-id="6d716-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="6d716-159">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6d716-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6d716-160">Kontrakt ujawniany jest ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="6d716-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d716-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d716-161">Requirements</span></span>  
  
|<span data-ttu-id="6d716-162">MOF</span><span class="sxs-lookup"><span data-stu-id="6d716-162">MOF</span></span>|<span data-ttu-id="6d716-163">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6d716-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6d716-164">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="6d716-164">Namespace</span></span>|<span data-ttu-id="6d716-165">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6d716-165">Defined in root\ServiceModel</span></span>|

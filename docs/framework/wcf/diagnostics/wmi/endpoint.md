---
title: "Punkt końcowy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef4e27f6e7a45fe705aa09827702a64c960b6a16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint"></a><span data-ttu-id="306e7-102">Punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="306e7-102">Endpoint</span></span>
<span data-ttu-id="306e7-103">Punkt końcowy</span><span class="sxs-lookup"><span data-stu-id="306e7-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="306e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="306e7-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="306e7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="306e7-105">Methods</span></span>  
 <span data-ttu-id="306e7-106">Klasa punktu końcowego definiuje następującą metodę.</span><span class="sxs-lookup"><span data-stu-id="306e7-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="306e7-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="306e7-107">Method</span></span>|<span data-ttu-id="306e7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="306e7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="306e7-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="306e7-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="306e7-110">Pobiera nazwę wystąpienia licznika wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="306e7-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="306e7-111">Właściwości</span><span class="sxs-lookup"><span data-stu-id="306e7-111">Properties</span></span>  
 <span data-ttu-id="306e7-112">Klasa punkt końcowy ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="306e7-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="306e7-113">Adres</span><span class="sxs-lookup"><span data-stu-id="306e7-113">Address</span></span>  
 <span data-ttu-id="306e7-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="306e7-114">Data type: string</span></span>  
  
 <span data-ttu-id="306e7-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-116">Identyfikator URI zawierający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="306e7-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="306e7-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="306e7-117">AddressHeaders</span></span>  
 <span data-ttu-id="306e7-118">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="306e7-118">Data type: string array</span></span>  
  
 <span data-ttu-id="306e7-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-120">Kolekcja nagłówków adresu przyłączonych do tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="306e7-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="306e7-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="306e7-121">AddressIdentity</span></span>  
 <span data-ttu-id="306e7-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="306e7-122">Data type: string</span></span>  
  
 <span data-ttu-id="306e7-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-124">Tożsamość punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="306e7-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="306e7-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="306e7-125">AppDomainId</span></span>  
 <span data-ttu-id="306e7-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="306e7-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="306e7-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-128">Identyfikator domeny aplikacji obsługującej punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="306e7-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="306e7-129">Zachowania</span><span class="sxs-lookup"><span data-stu-id="306e7-129">Behaviors</span></span>  
 <span data-ttu-id="306e7-130">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="306e7-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="306e7-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-132">Kolekcja zachowań implementowanych przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="306e7-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="306e7-133">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="306e7-133">Binding</span></span>  
 <span data-ttu-id="306e7-134">Typ danych: powiązanie</span><span class="sxs-lookup"><span data-stu-id="306e7-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="306e7-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-136">Powiązanie używane przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="306e7-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="306e7-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="306e7-137">ContractName</span></span>  
 <span data-ttu-id="306e7-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="306e7-138">Data type: string</span></span>  
  
 <span data-ttu-id="306e7-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-140">Ciąg określający, który kontrakt jest ujawniany ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="306e7-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="306e7-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="306e7-141">CounterInstanceName</span></span>  
 <span data-ttu-id="306e7-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="306e7-142">Data type: string</span></span>  
  
 <span data-ttu-id="306e7-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-144">Nazwa wystąpienia liczników wydajności punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="306e7-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="306e7-145">Identyfikator ListenUri</span><span class="sxs-lookup"><span data-stu-id="306e7-145">ListenUri</span></span>  
 <span data-ttu-id="306e7-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="306e7-146">Data type: string</span></span>  
  
 <span data-ttu-id="306e7-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-148">Identyfikator Uri punktu końcowego nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="306e7-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="306e7-149">Nazwa</span><span class="sxs-lookup"><span data-stu-id="306e7-149">Name</span></span>  
 <span data-ttu-id="306e7-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="306e7-150">Data type: string</span></span>  
  
 <span data-ttu-id="306e7-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-152">Unikatowa nazwa tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="306e7-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="306e7-153">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="306e7-153">ProcessId</span></span>  
 <span data-ttu-id="306e7-154">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="306e7-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="306e7-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-156">Identyfikator procesu obsługującego punkt końcowy procesu.</span><span class="sxs-lookup"><span data-stu-id="306e7-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="306e7-157">ref</span><span class="sxs-lookup"><span data-stu-id="306e7-157">ref</span></span>  
 <span data-ttu-id="306e7-158">Typ danych: kontraktu</span><span class="sxs-lookup"><span data-stu-id="306e7-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="306e7-159">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="306e7-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="306e7-160">Kontrakt ujawniany jest ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="306e7-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="306e7-161">Wymagania</span><span class="sxs-lookup"><span data-stu-id="306e7-161">Requirements</span></span>  
  
|<span data-ttu-id="306e7-162">MOF</span><span class="sxs-lookup"><span data-stu-id="306e7-162">MOF</span></span>|<span data-ttu-id="306e7-163">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="306e7-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="306e7-164">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="306e7-164">Namespace</span></span>|<span data-ttu-id="306e7-165">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="306e7-165">Defined in root\ServiceModel</span></span>|

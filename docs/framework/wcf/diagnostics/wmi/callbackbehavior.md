---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 2854671eaabb37066b57d87a7496183c9e5bba4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562856"
---
# <a name="callbackbehavior"></a><span data-ttu-id="aaccd-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="aaccd-102">CallbackBehavior</span></span>
<span data-ttu-id="aaccd-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="aaccd-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaccd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaccd-104">Syntax</span></span>  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="aaccd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="aaccd-105">Methods</span></span>  
 <span data-ttu-id="aaccd-106">Klasa CallbackBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="aaccd-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aaccd-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="aaccd-107">Properties</span></span>  
 <span data-ttu-id="aaccd-108">Klasa CallbackBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="aaccd-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="aaccd-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="aaccd-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="aaccd-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aaccd-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="aaccd-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aaccd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aaccd-112">W przypadku wartości true automatycznie zamknięciem sesji usługi powoduje zamknięcie sesji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="aaccd-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="aaccd-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="aaccd-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="aaccd-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="aaccd-114">Data type: string</span></span>  
<span data-ttu-id="aaccd-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aaccd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aaccd-116">Określa, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="aaccd-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="aaccd-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="aaccd-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="aaccd-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aaccd-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="aaccd-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aaccd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aaccd-120">Wartość, która określa, czy wysyłać dane serializacji nieznany podczas transmisji.</span><span class="sxs-lookup"><span data-stu-id="aaccd-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="aaccd-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="aaccd-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="aaccd-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aaccd-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="aaccd-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aaccd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aaccd-124">Po włączeniu szczegóły dotyczące wyjątków w wywołaniu zwrotnym są dołączane do błędów zwracanych do usługi.</span><span class="sxs-lookup"><span data-stu-id="aaccd-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="aaccd-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="aaccd-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="aaccd-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aaccd-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="aaccd-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aaccd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aaccd-128">Maksymalną liczbę elementów dozwoloną w Zserializowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="aaccd-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="aaccd-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="aaccd-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="aaccd-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aaccd-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="aaccd-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aaccd-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aaccd-132">Określa, czy umożliwia wybieranie wątkiem wykonywania w bieżącym kontekście synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="aaccd-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="aaccd-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="aaccd-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="aaccd-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aaccd-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="aaccd-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aaccd-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aaccd-136">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="aaccd-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaccd-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aaccd-137">Requirements</span></span>  
  
|<span data-ttu-id="aaccd-138">MOF</span><span class="sxs-lookup"><span data-stu-id="aaccd-138">MOF</span></span>|<span data-ttu-id="aaccd-139">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="aaccd-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aaccd-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="aaccd-140">Namespace</span></span>|<span data-ttu-id="aaccd-141">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aaccd-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aaccd-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aaccd-142">See also</span></span>
- <xref:System.ServiceModel.CallbackBehaviorAttribute>

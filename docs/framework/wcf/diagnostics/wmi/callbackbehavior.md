---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 9d8f4335c304d164daafeb0ad4de5b4e3bba4590
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963959"
---
# <a name="callbackbehavior"></a><span data-ttu-id="33f96-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="33f96-102">CallbackBehavior</span></span>
<span data-ttu-id="33f96-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="33f96-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f96-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33f96-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="33f96-105">Metody</span><span class="sxs-lookup"><span data-stu-id="33f96-105">Methods</span></span>  
 <span data-ttu-id="33f96-106">Klasa CallbackBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="33f96-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="33f96-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="33f96-107">Properties</span></span>  
 <span data-ttu-id="33f96-108">Klasa CallbackBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="33f96-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="33f96-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="33f96-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="33f96-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="33f96-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="33f96-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="33f96-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33f96-112">W przypadku wartości true automatycznie zamknięciem sesji usługi powoduje zamknięcie sesji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="33f96-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="33f96-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="33f96-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="33f96-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="33f96-114">Data type: string</span></span>  
<span data-ttu-id="33f96-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="33f96-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33f96-116">Określa, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="33f96-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="33f96-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="33f96-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="33f96-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="33f96-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="33f96-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="33f96-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33f96-120">Wartość, która określa, czy wysyłać dane serializacji nieznany podczas transmisji.</span><span class="sxs-lookup"><span data-stu-id="33f96-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="33f96-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="33f96-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="33f96-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="33f96-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="33f96-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="33f96-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33f96-124">Po włączeniu szczegóły dotyczące wyjątków w wywołaniu zwrotnym są dołączane do błędów zwracanych do usługi.</span><span class="sxs-lookup"><span data-stu-id="33f96-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="33f96-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="33f96-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="33f96-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="33f96-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="33f96-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="33f96-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33f96-128">Maksymalną liczbę elementów dozwoloną w Zserializowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="33f96-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="33f96-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="33f96-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="33f96-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="33f96-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="33f96-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="33f96-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33f96-132">Określa, czy umożliwia wybieranie wątkiem wykonywania w bieżącym kontekście synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="33f96-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="33f96-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="33f96-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="33f96-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="33f96-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="33f96-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="33f96-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33f96-136">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="33f96-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f96-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33f96-137">Requirements</span></span>  
  
|<span data-ttu-id="33f96-138">MOF</span><span class="sxs-lookup"><span data-stu-id="33f96-138">MOF</span></span>|<span data-ttu-id="33f96-139">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="33f96-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="33f96-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="33f96-140">Namespace</span></span>|<span data-ttu-id="33f96-141">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="33f96-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33f96-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33f96-142">See also</span></span>

- <xref:System.ServiceModel.CallbackBehaviorAttribute>

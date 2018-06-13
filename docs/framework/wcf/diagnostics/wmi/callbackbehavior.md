---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 2755ac4f365536366b41e743110ce494063a5ecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486963"
---
# <a name="callbackbehavior"></a><span data-ttu-id="1322a-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="1322a-102">CallbackBehavior</span></span>
<span data-ttu-id="1322a-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="1322a-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1322a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1322a-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="1322a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1322a-105">Methods</span></span>  
 <span data-ttu-id="1322a-106">Klasa CallbackBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="1322a-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1322a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1322a-107">Properties</span></span>  
 <span data-ttu-id="1322a-108">Klasa CallbackBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1322a-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="1322a-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="1322a-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="1322a-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1322a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="1322a-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1322a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1322a-112">Gdy ma wartość true, sesja jest automatycznie zamykana przy usługi zamknięciu sesji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="1322a-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="1322a-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="1322a-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="1322a-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1322a-114">Data type: string</span></span>  
<span data-ttu-id="1322a-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1322a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1322a-116">Określa, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="1322a-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="1322a-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="1322a-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="1322a-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1322a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1322a-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1322a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1322a-120">Wartość, która określa, czy nieznane dane serializacji serializacji.</span><span class="sxs-lookup"><span data-stu-id="1322a-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="1322a-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="1322a-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="1322a-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1322a-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1322a-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1322a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1322a-124">Po włączeniu szczegóły dotyczące wyjątków w wywołaniu zwrotnym są dołączane do błędów zwracanych do usługi.</span><span class="sxs-lookup"><span data-stu-id="1322a-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="1322a-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="1322a-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="1322a-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1322a-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="1322a-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1322a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1322a-128">Maksymalną liczbę elementów dozwoloną w obiekcie szeregowanym.</span><span class="sxs-lookup"><span data-stu-id="1322a-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="1322a-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="1322a-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="1322a-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1322a-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="1322a-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1322a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1322a-132">Określa, czy ma być używany bieżący kontekst synchronizacji do wyboru wątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="1322a-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="1322a-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="1322a-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="1322a-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1322a-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="1322a-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1322a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1322a-136">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="1322a-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1322a-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1322a-137">Requirements</span></span>  
  
|<span data-ttu-id="1322a-138">MOF</span><span class="sxs-lookup"><span data-stu-id="1322a-138">MOF</span></span>|<span data-ttu-id="1322a-139">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1322a-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1322a-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1322a-140">Namespace</span></span>|<span data-ttu-id="1322a-141">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1322a-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1322a-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1322a-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>

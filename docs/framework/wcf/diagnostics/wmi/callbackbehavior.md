---
title: CallbackBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5387e197cdf26a393ba23fd5696eb095dfd17a70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="9acd1-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="9acd1-102">CallbackBehavior</span></span>
<span data-ttu-id="9acd1-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="9acd1-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9acd1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9acd1-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9acd1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9acd1-105">Methods</span></span>  
 <span data-ttu-id="9acd1-106">Klasa CallbackBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="9acd1-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9acd1-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9acd1-107">Properties</span></span>  
 <span data-ttu-id="9acd1-108">Klasa CallbackBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="9acd1-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="9acd1-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="9acd1-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="9acd1-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9acd1-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="9acd1-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9acd1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9acd1-112">Gdy ma wartość true, sesja jest automatycznie zamykana przy usługi zamknięciu sesji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="9acd1-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="9acd1-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="9acd1-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="9acd1-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9acd1-114">Data type: string</span></span>  
<span data-ttu-id="9acd1-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9acd1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9acd1-116">Określa, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="9acd1-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="9acd1-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="9acd1-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="9acd1-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9acd1-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="9acd1-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9acd1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9acd1-120">Wartość, która określa, czy nieznane dane serializacji serializacji.</span><span class="sxs-lookup"><span data-stu-id="9acd1-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="9acd1-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="9acd1-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="9acd1-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9acd1-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="9acd1-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9acd1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9acd1-124">Po włączeniu szczegóły dotyczące wyjątków w wywołaniu zwrotnym są dołączane do błędów zwracanych do usługi.</span><span class="sxs-lookup"><span data-stu-id="9acd1-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="9acd1-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="9acd1-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="9acd1-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9acd1-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="9acd1-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9acd1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9acd1-128">Maksymalną liczbę elementów dozwoloną w obiekcie szeregowanym.</span><span class="sxs-lookup"><span data-stu-id="9acd1-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="9acd1-129">UseSynchronizationContext elementu</span><span class="sxs-lookup"><span data-stu-id="9acd1-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="9acd1-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9acd1-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="9acd1-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9acd1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9acd1-132">Określa, czy ma być używany bieżący kontekst synchronizacji do wyboru wątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="9acd1-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="9acd1-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="9acd1-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="9acd1-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9acd1-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="9acd1-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9acd1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9acd1-136">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9acd1-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9acd1-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9acd1-137">Requirements</span></span>  
  
|<span data-ttu-id="9acd1-138">MOF</span><span class="sxs-lookup"><span data-stu-id="9acd1-138">MOF</span></span>|<span data-ttu-id="9acd1-139">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9acd1-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9acd1-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="9acd1-140">Namespace</span></span>|<span data-ttu-id="9acd1-141">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9acd1-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9acd1-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9acd1-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>

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
ms.openlocfilehash: 7c10d9e26f86fa569b1a607c9b755f32ee97792a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="a4094-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="a4094-102">CallbackBehavior</span></span>
<span data-ttu-id="a4094-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="a4094-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4094-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4094-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a4094-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a4094-105">Methods</span></span>  
 <span data-ttu-id="a4094-106">Klasa CallbackBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="a4094-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a4094-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a4094-107">Properties</span></span>  
 <span data-ttu-id="a4094-108">Klasa CallbackBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a4094-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="a4094-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="a4094-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="a4094-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4094-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4094-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4094-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-112">Gdy ma wartość true, sesja jest automatycznie zamykana przy usługi zamknięciu sesji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="a4094-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="a4094-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="a4094-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="a4094-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a4094-114">Data type: string</span></span>  
<span data-ttu-id="a4094-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4094-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-116">Określa, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="a4094-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="a4094-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="a4094-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="a4094-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4094-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4094-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4094-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-120">Wartość, która określa, czy nieznane dane serializacji serializacji.</span><span class="sxs-lookup"><span data-stu-id="a4094-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="a4094-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="a4094-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="a4094-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4094-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4094-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4094-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-124">Po włączeniu szczegóły dotyczące wyjątków w wywołaniu zwrotnym są dołączane do błędów zwracanych do usługi.</span><span class="sxs-lookup"><span data-stu-id="a4094-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="a4094-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="a4094-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="a4094-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4094-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4094-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4094-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-128">Maksymalną liczbę elementów dozwoloną w obiekcie szeregowanym.</span><span class="sxs-lookup"><span data-stu-id="a4094-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="a4094-129">UseSynchronizationContext elementu</span><span class="sxs-lookup"><span data-stu-id="a4094-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="a4094-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4094-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4094-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4094-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-132">Określa, czy ma być używany bieżący kontekst synchronizacji do wyboru wątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a4094-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="a4094-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="a4094-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="a4094-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4094-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4094-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4094-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-136">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a4094-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4094-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4094-137">Requirements</span></span>  
  
|<span data-ttu-id="a4094-138">MOF</span><span class="sxs-lookup"><span data-stu-id="a4094-138">MOF</span></span>|<span data-ttu-id="a4094-139">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a4094-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a4094-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="a4094-140">Namespace</span></span>|<span data-ttu-id="a4094-141">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a4094-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4094-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4094-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>

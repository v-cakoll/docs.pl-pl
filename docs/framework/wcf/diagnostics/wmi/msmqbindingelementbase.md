---
title: MsmqBindingElementBase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b70b4b4a1529085cba8625598f56a9eece07e866
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="fc1ba-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="fc1ba-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="fc1ba-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="fc1ba-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc1ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc1ba-104">Syntax</span></span>  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fc1ba-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fc1ba-105">Methods</span></span>  
 <span data-ttu-id="fc1ba-106">Klasa MsmqBindingElementBase nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fc1ba-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fc1ba-107">Properties</span></span>  
 <span data-ttu-id="fc1ba-108">Klasa MsmqBindingElementBase ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fc1ba-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="fc1ba-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="fc1ba-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="fc1ba-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fc1ba-110">Data type: string</span></span>  
  
 <span data-ttu-id="fc1ba-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-112">Identyfikator URI zawiera lokalizację kolejki utraconych wiadomości dla każdej aplikacji, gdzie umieścić są komunikaty wygasłe, lub które nie przeszły przesłanie bądź dostarczenie.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="fc1ba-113">DeadLetterQueue wartość</span><span class="sxs-lookup"><span data-stu-id="fc1ba-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="fc1ba-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fc1ba-114">Data type: string</span></span>  
  
 <span data-ttu-id="fc1ba-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-116">Wartość wyliczenia wskazująca typ używanej kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="fc1ba-117">trwałe</span><span class="sxs-lookup"><span data-stu-id="fc1ba-117">Durable</span></span>  
 <span data-ttu-id="fc1ba-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fc1ba-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="fc1ba-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-120">Wartość, która wskazuje, czy komunikaty przetwarzane przez to powiązanie są trwałe lub zmienne.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="fc1ba-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="fc1ba-121">ExactlyOnce</span></span>  
 <span data-ttu-id="fc1ba-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fc1ba-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="fc1ba-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-124">Wartość logiczna wskazująca, czy komunikaty przetwarzane przez to powiązanie są odbierane dokładnie raz.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="fc1ba-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="fc1ba-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="fc1ba-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="fc1ba-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="fc1ba-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-128">Maksymalna liczba cykli ponawiania próby dostarczenia komunikatów do aplikacji odbierającej.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="fc1ba-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="fc1ba-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="fc1ba-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fc1ba-130">Data type: string</span></span>  
  
 <span data-ttu-id="fc1ba-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-132">Ustawienia dotyczące obsługi uszkodzonych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="fc1ba-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="fc1ba-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="fc1ba-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="fc1ba-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="fc1ba-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-136">Maksymalna liczba natychmiastowego ponawiania prób w przypadku komunikatu odczytywanego z kolejki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="fc1ba-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="fc1ba-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="fc1ba-138">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="fc1ba-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="fc1ba-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-140">Wartość wskazująca zwłokę między kolejnymi próbami dostarczenia komunikatu, którego nie można było dostarczyć natychmiast.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="fc1ba-141">Wartość TimeToLive</span><span class="sxs-lookup"><span data-stu-id="fc1ba-141">TimeToLive</span></span>  
 <span data-ttu-id="fc1ba-142">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="fc1ba-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="fc1ba-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-144">Przedział czasu, która wskazuje, jak długo komunikaty przetwarzane przez to powiązanie mogą znajdować się w kolejce, zanim wygasną.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="fc1ba-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="fc1ba-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="fc1ba-146">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fc1ba-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="fc1ba-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-148">Wartość logiczna, która wskazuje, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="fc1ba-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="fc1ba-149">UseSourceJournal</span></span>  
 <span data-ttu-id="fc1ba-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fc1ba-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="fc1ba-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fc1ba-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc1ba-152">Wartość logiczna wskazująca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc1ba-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc1ba-153">Requirements</span></span>  
  
|<span data-ttu-id="fc1ba-154">MOF</span><span class="sxs-lookup"><span data-stu-id="fc1ba-154">MOF</span></span>|<span data-ttu-id="fc1ba-155">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fc1ba-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fc1ba-156">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fc1ba-156">Namespace</span></span>|<span data-ttu-id="fc1ba-157">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fc1ba-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc1ba-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc1ba-158">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>

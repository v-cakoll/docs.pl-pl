---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: e7f4cf41168bd1e5483524195e20541d896a6569
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183194"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="b25ff-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="b25ff-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="b25ff-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="b25ff-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b25ff-104">Syntax</span></span>  
  
```csharp  
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
  
## <a name="methods"></a><span data-ttu-id="b25ff-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b25ff-105">Methods</span></span>  
 <span data-ttu-id="b25ff-106">Klasa MsmqBindingElementBase nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b25ff-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b25ff-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b25ff-107">Properties</span></span>  
 <span data-ttu-id="b25ff-108">Klasa MsmqBindingElementBase ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b25ff-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="b25ff-109">customDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="b25ff-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="b25ff-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b25ff-110">Data type: string</span></span>  
  
 <span data-ttu-id="b25ff-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-112">Identyfikator URI, który zawiera lokalizację kolejki utraconych wiadomości dla każdej aplikacji, gdzie umieszcza komunikaty wygasły lub mają niepowodzeniem transferu lub dostarczania.</span><span class="sxs-lookup"><span data-stu-id="b25ff-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="b25ff-113">DeadLetterQueue wartość</span><span class="sxs-lookup"><span data-stu-id="b25ff-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="b25ff-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b25ff-114">Data type: string</span></span>  
  
 <span data-ttu-id="b25ff-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-116">Wartość wyliczenia, który wskazuje na typ używanej kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b25ff-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="b25ff-117">trwałe</span><span class="sxs-lookup"><span data-stu-id="b25ff-117">Durable</span></span>  
 <span data-ttu-id="b25ff-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b25ff-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b25ff-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-120">Wartość, która wskazuje, czy komunikaty przetwarzane przez to powiązanie są trwałe lub zmienne.</span><span class="sxs-lookup"><span data-stu-id="b25ff-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="b25ff-121">exactlyOnce</span><span class="sxs-lookup"><span data-stu-id="b25ff-121">ExactlyOnce</span></span>  
 <span data-ttu-id="b25ff-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b25ff-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="b25ff-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-124">Wartość logiczna wskazująca, czy komunikaty przetwarzane przez to powiązanie są odbierane dokładnie raz.</span><span class="sxs-lookup"><span data-stu-id="b25ff-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="b25ff-125">maxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="b25ff-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="b25ff-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b25ff-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="b25ff-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-128">Maksymalna liczba ponownych prób cyklów próby dostarczenia komunikatów do aplikacji odbierającej.</span><span class="sxs-lookup"><span data-stu-id="b25ff-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="b25ff-129">receiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="b25ff-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="b25ff-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b25ff-130">Data type: string</span></span>  
  
 <span data-ttu-id="b25ff-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-132">Ustawienia obsługi Zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="b25ff-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="b25ff-133">receiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="b25ff-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="b25ff-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b25ff-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="b25ff-135">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-136">Maksymalna liczba natychmiastowego ponawiania próby w wiadomości, które są odczytywane z kolejki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b25ff-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="b25ff-137">retryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="b25ff-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="b25ff-138">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="b25ff-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="b25ff-139">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-140">Wartość wskazująca czas opóźnienia między cykle przy próbie dostarczenia komunikatu, którego nie można dostarczyć natychmiast.</span><span class="sxs-lookup"><span data-stu-id="b25ff-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="b25ff-141">timeToLive</span><span class="sxs-lookup"><span data-stu-id="b25ff-141">TimeToLive</span></span>  
 <span data-ttu-id="b25ff-142">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="b25ff-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="b25ff-143">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-144">Przedział czasu, która wskazuje, jak długo komunikaty przetwarzane przez to powiązanie mogą znajdować się w kolejce, zanim wygasną.</span><span class="sxs-lookup"><span data-stu-id="b25ff-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="b25ff-145">useMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="b25ff-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="b25ff-146">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b25ff-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="b25ff-147">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-148">Wartość logiczna, która wskazuje, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone.</span><span class="sxs-lookup"><span data-stu-id="b25ff-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="b25ff-149">useSourceJournal</span><span class="sxs-lookup"><span data-stu-id="b25ff-149">UseSourceJournal</span></span>  
 <span data-ttu-id="b25ff-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b25ff-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="b25ff-151">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b25ff-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b25ff-152">Wartość logiczna wskazująca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła.</span><span class="sxs-lookup"><span data-stu-id="b25ff-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b25ff-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b25ff-153">Requirements</span></span>  
  
|<span data-ttu-id="b25ff-154">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="b25ff-154">MOF</span></span>|<span data-ttu-id="b25ff-155">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b25ff-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b25ff-156">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b25ff-156">Namespace</span></span>|<span data-ttu-id="b25ff-157">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b25ff-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b25ff-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b25ff-158">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>

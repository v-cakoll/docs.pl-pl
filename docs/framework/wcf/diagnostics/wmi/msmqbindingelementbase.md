---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 1df4b32feda246a536183a42ac11b113bc4bb259
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963439"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="98764-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="98764-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="98764-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="98764-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98764-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="98764-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="98764-105">Metody</span><span class="sxs-lookup"><span data-stu-id="98764-105">Methods</span></span>  
 <span data-ttu-id="98764-106">Klasa MsmqBindingElementBase nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="98764-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="98764-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="98764-107">Properties</span></span>  
 <span data-ttu-id="98764-108">Klasa MsmqBindingElementBase ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="98764-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="98764-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="98764-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="98764-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="98764-110">Data type: string</span></span>  
  
 <span data-ttu-id="98764-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-112">Identyfikator URI, który zawiera lokalizację kolejki utraconych wiadomości dla każdej aplikacji, gdzie umieszcza komunikaty wygasły lub mają niepowodzeniem transferu lub dostarczania.</span><span class="sxs-lookup"><span data-stu-id="98764-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="98764-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="98764-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="98764-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="98764-114">Data type: string</span></span>  
  
 <span data-ttu-id="98764-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-116">Wartość wyliczenia, który wskazuje na typ używanej kolejki utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="98764-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="98764-117">trwałe</span><span class="sxs-lookup"><span data-stu-id="98764-117">Durable</span></span>  
 <span data-ttu-id="98764-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="98764-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="98764-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-120">Wartość, która wskazuje, czy komunikaty przetwarzane przez to powiązanie są trwałe lub zmienne.</span><span class="sxs-lookup"><span data-stu-id="98764-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="98764-121">exactlyOnce</span><span class="sxs-lookup"><span data-stu-id="98764-121">ExactlyOnce</span></span>  
 <span data-ttu-id="98764-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="98764-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="98764-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-124">Wartość logiczna wskazująca, czy komunikaty przetwarzane przez to powiązanie są odbierane dokładnie raz.</span><span class="sxs-lookup"><span data-stu-id="98764-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="98764-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="98764-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="98764-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="98764-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="98764-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-128">Maksymalna liczba ponownych prób cyklów próby dostarczenia komunikatów do aplikacji odbierającej.</span><span class="sxs-lookup"><span data-stu-id="98764-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="98764-129">receiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="98764-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="98764-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="98764-130">Data type: string</span></span>  
  
 <span data-ttu-id="98764-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-132">Ustawienia obsługi Zarządzanie skażonymi komunikatami.</span><span class="sxs-lookup"><span data-stu-id="98764-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="98764-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="98764-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="98764-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="98764-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="98764-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-136">Maksymalna liczba natychmiastowego ponawiania próby w wiadomości, które są odczytywane z kolejki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98764-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="98764-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="98764-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="98764-138">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="98764-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="98764-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-140">Wartość wskazująca czas opóźnienia między cykle przy próbie dostarczenia komunikatu, którego nie można dostarczyć natychmiast.</span><span class="sxs-lookup"><span data-stu-id="98764-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="98764-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="98764-141">TimeToLive</span></span>  
 <span data-ttu-id="98764-142">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="98764-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="98764-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-144">Przedział czasu, która wskazuje, jak długo komunikaty przetwarzane przez to powiązanie mogą znajdować się w kolejce, zanim wygasną.</span><span class="sxs-lookup"><span data-stu-id="98764-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="98764-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="98764-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="98764-146">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="98764-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="98764-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-148">Wartość logiczna, która wskazuje, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone.</span><span class="sxs-lookup"><span data-stu-id="98764-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="98764-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="98764-149">UseSourceJournal</span></span>  
 <span data-ttu-id="98764-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="98764-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="98764-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="98764-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98764-152">Wartość logiczna wskazująca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła.</span><span class="sxs-lookup"><span data-stu-id="98764-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98764-153">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98764-153">Requirements</span></span>  
  
|<span data-ttu-id="98764-154">MOF</span><span class="sxs-lookup"><span data-stu-id="98764-154">MOF</span></span>|<span data-ttu-id="98764-155">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="98764-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="98764-156">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="98764-156">Namespace</span></span>|<span data-ttu-id="98764-157">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="98764-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98764-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98764-158">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>

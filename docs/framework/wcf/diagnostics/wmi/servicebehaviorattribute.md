---
title: ServiceBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6b0620e9cb2575bcfe9cd6f01b5d87669df69b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="19799-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="19799-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="19799-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="19799-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19799-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19799-104">Syntax</span></span>  
  
```  
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="19799-105">Metody</span><span class="sxs-lookup"><span data-stu-id="19799-105">Methods</span></span>  
 <span data-ttu-id="19799-106">Klasa atrybutu ServiceBehaviorAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="19799-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="19799-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="19799-107">Properties</span></span>  
 <span data-ttu-id="19799-108">Klasa atrybutu ServiceBehaviorAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="19799-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="19799-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="19799-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="19799-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="19799-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="19799-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-112">Wskazuje, czy automatycznie zamykać sesję przy zamykaniu przez klienta sesji wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="19799-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="19799-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="19799-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="19799-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="19799-114">Data type: string</span></span>  
<span data-ttu-id="19799-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-116">Wskazuje, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="19799-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="19799-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="19799-117">ConfigurationName</span></span>  
 <span data-ttu-id="19799-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="19799-118">Data type: string</span></span>  
  
 <span data-ttu-id="19799-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-120">Nazwa konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="19799-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="19799-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="19799-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="19799-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="19799-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="19799-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-124">Określa, czy nieznane dane serializacji serializacji.</span><span class="sxs-lookup"><span data-stu-id="19799-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="19799-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="19799-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="19799-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="19799-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="19799-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-128">Określa, czy dołączać informacje o zarządzanym wyjątku w informacjach szczegółowych o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="19799-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="19799-129">Właściwość InstanceContextMode obiektu</span><span class="sxs-lookup"><span data-stu-id="19799-129">InstanceContextMode</span></span>  
 <span data-ttu-id="19799-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="19799-130">Data type: string</span></span>  
  
 <span data-ttu-id="19799-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-132">Określa, kiedy tworzony jest nowy obiekt usługi.</span><span class="sxs-lookup"><span data-stu-id="19799-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="19799-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="19799-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="19799-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="19799-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="19799-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-136">Maksymalną liczbę elementów dozwoloną w obiekcie szeregowanym.</span><span class="sxs-lookup"><span data-stu-id="19799-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="19799-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="19799-137">Name</span></span>  
 <span data-ttu-id="19799-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="19799-138">Data type: string</span></span>  
  
 <span data-ttu-id="19799-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-140">Atrybut nazwy usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="19799-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="19799-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="19799-141">Namespace</span></span>  
 <span data-ttu-id="19799-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="19799-142">Data type: string</span></span>  
  
 <span data-ttu-id="19799-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-144">Docelowy obszar nazw usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="19799-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="19799-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="19799-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="19799-146">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="19799-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="19799-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-148">Określa, czy obiekt usługi jest ponownie przetwarzany po zakończeniu bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="19799-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="19799-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="19799-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="19799-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="19799-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="19799-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-152">Określa, czy transakcje oczekujące są kończone podczas zamykania bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="19799-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="19799-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="19799-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="19799-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="19799-154">Data type: string</span></span>  
  
 <span data-ttu-id="19799-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-156">Określa poziom izolacji transakcji.</span><span class="sxs-lookup"><span data-stu-id="19799-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="19799-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="19799-157">TransactionTimeout</span></span>  
 <span data-ttu-id="19799-158">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="19799-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="19799-159">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-160">Okres, w ramach którego transakcja musi zostać zakończona.</span><span class="sxs-lookup"><span data-stu-id="19799-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="19799-161">UseSynchronizationContext elementu</span><span class="sxs-lookup"><span data-stu-id="19799-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="19799-162">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="19799-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="19799-163">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-164">Określa, czy używać kontekstu synchronizacji do wybierania kolejności wykonywania wątków.</span><span class="sxs-lookup"><span data-stu-id="19799-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="19799-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="19799-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="19799-166">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="19799-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="19799-167">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="19799-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="19799-168">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="19799-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19799-169">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19799-169">Requirements</span></span>  
  
|<span data-ttu-id="19799-170">MOF</span><span class="sxs-lookup"><span data-stu-id="19799-170">MOF</span></span>|<span data-ttu-id="19799-171">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="19799-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="19799-172">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="19799-172">Namespace</span></span>|<span data-ttu-id="19799-173">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="19799-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19799-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19799-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>

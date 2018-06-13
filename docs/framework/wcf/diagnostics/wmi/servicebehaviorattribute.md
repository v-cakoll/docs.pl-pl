---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 514af4c6d9eaaf8929ca831e4e786c895d14c67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487202"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="fe72c-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="fe72c-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="fe72c-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="fe72c-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe72c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe72c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="fe72c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fe72c-105">Methods</span></span>  
 <span data-ttu-id="fe72c-106">Klasa atrybutu ServiceBehaviorAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fe72c-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fe72c-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fe72c-107">Properties</span></span>  
 <span data-ttu-id="fe72c-108">Klasa atrybutu ServiceBehaviorAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fe72c-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="fe72c-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="fe72c-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="fe72c-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe72c-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe72c-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-112">Wskazuje, czy automatycznie zamykać sesję przy zamykaniu przez klienta sesji wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="fe72c-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="fe72c-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="fe72c-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="fe72c-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe72c-114">Data type: string</span></span>  
<span data-ttu-id="fe72c-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-116">Wskazuje, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="fe72c-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="fe72c-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="fe72c-117">ConfigurationName</span></span>  
 <span data-ttu-id="fe72c-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe72c-118">Data type: string</span></span>  
  
 <span data-ttu-id="fe72c-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-120">Nazwa konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="fe72c-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="fe72c-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="fe72c-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="fe72c-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe72c-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe72c-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-124">Określa, czy nieznane dane serializacji serializacji.</span><span class="sxs-lookup"><span data-stu-id="fe72c-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="fe72c-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="fe72c-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="fe72c-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe72c-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe72c-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-128">Określa, czy dołączać informacje o zarządzanym wyjątku w informacjach szczegółowych o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="fe72c-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="fe72c-129">Właściwość InstanceContextMode obiektu</span><span class="sxs-lookup"><span data-stu-id="fe72c-129">InstanceContextMode</span></span>  
 <span data-ttu-id="fe72c-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe72c-130">Data type: string</span></span>  
  
 <span data-ttu-id="fe72c-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-132">Określa, kiedy tworzony jest nowy obiekt usługi.</span><span class="sxs-lookup"><span data-stu-id="fe72c-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="fe72c-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="fe72c-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="fe72c-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="fe72c-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="fe72c-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-136">Maksymalną liczbę elementów dozwoloną w obiekcie szeregowanym.</span><span class="sxs-lookup"><span data-stu-id="fe72c-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="fe72c-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fe72c-137">Name</span></span>  
 <span data-ttu-id="fe72c-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe72c-138">Data type: string</span></span>  
  
 <span data-ttu-id="fe72c-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-140">Atrybut nazwy usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="fe72c-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="fe72c-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fe72c-141">Namespace</span></span>  
 <span data-ttu-id="fe72c-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe72c-142">Data type: string</span></span>  
  
 <span data-ttu-id="fe72c-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-144">Docelowy obszar nazw usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="fe72c-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="fe72c-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="fe72c-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="fe72c-146">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe72c-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe72c-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-148">Określa, czy obiekt usługi jest ponownie przetwarzany po zakończeniu bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="fe72c-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="fe72c-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="fe72c-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="fe72c-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe72c-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe72c-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-152">Określa, czy transakcje oczekujące są kończone podczas zamykania bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="fe72c-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="fe72c-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="fe72c-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="fe72c-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe72c-154">Data type: string</span></span>  
  
 <span data-ttu-id="fe72c-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-156">Określa poziom izolacji transakcji.</span><span class="sxs-lookup"><span data-stu-id="fe72c-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="fe72c-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="fe72c-157">TransactionTimeout</span></span>  
 <span data-ttu-id="fe72c-158">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="fe72c-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="fe72c-159">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-160">Okres, w ramach którego transakcja musi zostać zakończona.</span><span class="sxs-lookup"><span data-stu-id="fe72c-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="fe72c-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="fe72c-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="fe72c-162">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe72c-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe72c-163">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-164">Określa, czy używać kontekstu synchronizacji do wybierania kolejności wykonywania wątków.</span><span class="sxs-lookup"><span data-stu-id="fe72c-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="fe72c-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="fe72c-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="fe72c-166">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe72c-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe72c-167">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe72c-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe72c-168">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="fe72c-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe72c-169">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe72c-169">Requirements</span></span>  
  
|<span data-ttu-id="fe72c-170">MOF</span><span class="sxs-lookup"><span data-stu-id="fe72c-170">MOF</span></span>|<span data-ttu-id="fe72c-171">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fe72c-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fe72c-172">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fe72c-172">Namespace</span></span>|<span data-ttu-id="fe72c-173">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fe72c-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe72c-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe72c-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>

---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: b6221e93f10b87a368bd594932a8c36ae14df8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206879"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="09a55-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="09a55-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="09a55-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="09a55-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09a55-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="09a55-105">Metody</span><span class="sxs-lookup"><span data-stu-id="09a55-105">Methods</span></span>  
 <span data-ttu-id="09a55-106">Klasa ServiceBehaviorAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="09a55-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="09a55-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="09a55-107">Properties</span></span>  
 <span data-ttu-id="09a55-108">Klasa ServiceBehaviorAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="09a55-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="09a55-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="09a55-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="09a55-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="09a55-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="09a55-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-112">Wskazuje, czy należy automatycznie Zamknij sesję, gdy klient zamyka sesję danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="09a55-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="09a55-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="09a55-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="09a55-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="09a55-114">Data type: string</span></span>  
<span data-ttu-id="09a55-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-116">Wskazuje, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="09a55-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="09a55-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="09a55-117">ConfigurationName</span></span>  
 <span data-ttu-id="09a55-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="09a55-118">Data type: string</span></span>  
  
 <span data-ttu-id="09a55-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-120">Nazwa konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="09a55-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="09a55-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="09a55-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="09a55-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="09a55-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="09a55-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-124">Określa, czy wysyłać dane serializacji nieznany podczas transmisji.</span><span class="sxs-lookup"><span data-stu-id="09a55-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="09a55-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="09a55-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="09a55-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="09a55-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="09a55-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-128">Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="09a55-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="09a55-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="09a55-129">InstanceContextMode</span></span>  
 <span data-ttu-id="09a55-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="09a55-130">Data type: string</span></span>  
  
 <span data-ttu-id="09a55-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-132">Określa, kiedy tworzony jest nowy obiekt usługi.</span><span class="sxs-lookup"><span data-stu-id="09a55-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="09a55-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="09a55-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="09a55-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="09a55-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="09a55-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-136">Maksymalną liczbę elementów dozwoloną w Zserializowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="09a55-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="09a55-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="09a55-137">Name</span></span>  
 <span data-ttu-id="09a55-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="09a55-138">Data type: string</span></span>  
  
 <span data-ttu-id="09a55-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-140">Atrybut nazwy usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="09a55-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="09a55-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="09a55-141">Namespace</span></span>  
 <span data-ttu-id="09a55-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="09a55-142">Data type: string</span></span>  
  
 <span data-ttu-id="09a55-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-144">Docelowy obszar nazw usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="09a55-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="09a55-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="09a55-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="09a55-146">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="09a55-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="09a55-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-148">Określa, czy obiekt usługi zostanie odtworzony po zakończeniu bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="09a55-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="09a55-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="09a55-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="09a55-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="09a55-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="09a55-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-152">Określa, czy oczekujące transakcje są wykonywane po zamknięciu bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="09a55-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="09a55-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="09a55-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="09a55-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="09a55-154">Data type: string</span></span>  
  
 <span data-ttu-id="09a55-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-156">Określa poziom izolacji transakcji.</span><span class="sxs-lookup"><span data-stu-id="09a55-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="09a55-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="09a55-157">TransactionTimeout</span></span>  
 <span data-ttu-id="09a55-158">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="09a55-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="09a55-159">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-160">Okres, w którym należy wykonać transakcję.</span><span class="sxs-lookup"><span data-stu-id="09a55-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="09a55-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="09a55-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="09a55-162">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="09a55-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="09a55-163">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-164">Określa, czy umożliwia wybieranie wykonywanie wątków w bieżącym kontekście synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="09a55-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="09a55-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="09a55-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="09a55-166">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="09a55-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="09a55-167">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="09a55-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09a55-168">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="09a55-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09a55-169">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09a55-169">Requirements</span></span>  
  
|<span data-ttu-id="09a55-170">MOF</span><span class="sxs-lookup"><span data-stu-id="09a55-170">MOF</span></span>|<span data-ttu-id="09a55-171">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="09a55-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="09a55-172">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="09a55-172">Namespace</span></span>|<span data-ttu-id="09a55-173">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="09a55-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09a55-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09a55-174">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>

---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: b6221e93f10b87a368bd594932a8c36ae14df8f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957017"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="a1a37-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="a1a37-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="a1a37-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="a1a37-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1a37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1a37-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a1a37-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a1a37-105">Methods</span></span>  
 <span data-ttu-id="a1a37-106">Klasa ServiceBehaviorAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="a1a37-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a1a37-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a1a37-107">Properties</span></span>  
 <span data-ttu-id="a1a37-108">Klasa ServiceBehaviorAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a1a37-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="a1a37-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="a1a37-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="a1a37-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1a37-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a37-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-112">Wskazuje, czy należy automatycznie Zamknij sesję, gdy klient zamyka sesję danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a1a37-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="a1a37-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="a1a37-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="a1a37-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a1a37-114">Data type: string</span></span>  
<span data-ttu-id="a1a37-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-116">Wskazuje, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="a1a37-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="a1a37-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="a1a37-117">ConfigurationName</span></span>  
 <span data-ttu-id="a1a37-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a1a37-118">Data type: string</span></span>  
  
 <span data-ttu-id="a1a37-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-120">Nazwa konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="a1a37-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="a1a37-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="a1a37-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="a1a37-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1a37-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a37-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-124">Określa, czy wysyłać dane serializacji nieznany podczas transmisji.</span><span class="sxs-lookup"><span data-stu-id="a1a37-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="a1a37-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="a1a37-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="a1a37-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1a37-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a37-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-128">Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="a1a37-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="a1a37-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="a1a37-129">InstanceContextMode</span></span>  
 <span data-ttu-id="a1a37-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a1a37-130">Data type: string</span></span>  
  
 <span data-ttu-id="a1a37-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-132">Określa, kiedy tworzony jest nowy obiekt usługi.</span><span class="sxs-lookup"><span data-stu-id="a1a37-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="a1a37-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="a1a37-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="a1a37-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="a1a37-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="a1a37-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-136">Maksymalną liczbę elementów dozwoloną w Zserializowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="a1a37-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="a1a37-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a1a37-137">Name</span></span>  
 <span data-ttu-id="a1a37-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a1a37-138">Data type: string</span></span>  
  
 <span data-ttu-id="a1a37-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-140">Atrybut nazwy usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="a1a37-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="a1a37-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="a1a37-141">Namespace</span></span>  
 <span data-ttu-id="a1a37-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a1a37-142">Data type: string</span></span>  
  
 <span data-ttu-id="a1a37-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-144">Docelowy obszar nazw usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="a1a37-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="a1a37-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="a1a37-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="a1a37-146">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1a37-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a37-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-148">Określa, czy obiekt usługi zostanie odtworzony po zakończeniu bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="a1a37-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="a1a37-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="a1a37-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="a1a37-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1a37-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a37-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-152">Określa, czy oczekujące transakcje są wykonywane po zamknięciu bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="a1a37-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="a1a37-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="a1a37-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="a1a37-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a1a37-154">Data type: string</span></span>  
  
 <span data-ttu-id="a1a37-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-156">Określa poziom izolacji transakcji.</span><span class="sxs-lookup"><span data-stu-id="a1a37-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="a1a37-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="a1a37-157">TransactionTimeout</span></span>  
 <span data-ttu-id="a1a37-158">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="a1a37-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="a1a37-159">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-160">Okres, w którym należy wykonać transakcję.</span><span class="sxs-lookup"><span data-stu-id="a1a37-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="a1a37-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="a1a37-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="a1a37-162">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1a37-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a37-163">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-164">Określa, czy umożliwia wybieranie wykonywanie wątków w bieżącym kontekście synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="a1a37-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="a1a37-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="a1a37-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="a1a37-166">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1a37-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1a37-167">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1a37-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1a37-168">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a1a37-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1a37-169">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1a37-169">Requirements</span></span>  
  
|<span data-ttu-id="a1a37-170">MOF</span><span class="sxs-lookup"><span data-stu-id="a1a37-170">MOF</span></span>|<span data-ttu-id="a1a37-171">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a1a37-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a1a37-172">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="a1a37-172">Namespace</span></span>|<span data-ttu-id="a1a37-173">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a1a37-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1a37-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1a37-174">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>

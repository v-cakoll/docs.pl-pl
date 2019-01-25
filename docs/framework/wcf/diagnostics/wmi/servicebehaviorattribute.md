---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 420686ebda7f23a5d883deece251b034147fafa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654584"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="fe7f7-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="fe7f7-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="fe7f7-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="fe7f7-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe7f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe7f7-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="fe7f7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fe7f7-105">Methods</span></span>  
 <span data-ttu-id="fe7f7-106">Klasa ServiceBehaviorAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fe7f7-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fe7f7-107">Properties</span></span>  
 <span data-ttu-id="fe7f7-108">Klasa ServiceBehaviorAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fe7f7-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="fe7f7-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="fe7f7-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="fe7f7-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe7f7-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe7f7-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-112">Wskazuje, czy należy automatycznie Zamknij sesję, gdy klient zamyka sesję danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="fe7f7-113">Właściwość ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="fe7f7-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="fe7f7-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7f7-114">Data type: string</span></span>  
<span data-ttu-id="fe7f7-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-116">Wskazuje, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="fe7f7-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="fe7f7-117">ConfigurationName</span></span>  
 <span data-ttu-id="fe7f7-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7f7-118">Data type: string</span></span>  
  
 <span data-ttu-id="fe7f7-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-120">Nazwa konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="fe7f7-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="fe7f7-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="fe7f7-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe7f7-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe7f7-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-124">Określa, czy wysyłać dane serializacji nieznany podczas transmisji.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="fe7f7-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="fe7f7-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="fe7f7-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe7f7-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe7f7-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-128">Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="fe7f7-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="fe7f7-129">InstanceContextMode</span></span>  
 <span data-ttu-id="fe7f7-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7f7-130">Data type: string</span></span>  
  
 <span data-ttu-id="fe7f7-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-132">Określa, kiedy tworzony jest nowy obiekt usługi.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="fe7f7-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="fe7f7-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="fe7f7-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="fe7f7-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="fe7f7-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-136">Maksymalną liczbę elementów dozwoloną w Zserializowany obiekt.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="fe7f7-137">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fe7f7-137">Name</span></span>  
 <span data-ttu-id="fe7f7-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7f7-138">Data type: string</span></span>  
  
 <span data-ttu-id="fe7f7-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-140">Atrybut nazwy usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="fe7f7-141">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fe7f7-141">Namespace</span></span>  
 <span data-ttu-id="fe7f7-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7f7-142">Data type: string</span></span>  
  
 <span data-ttu-id="fe7f7-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-144">Docelowy obszar nazw usługi w języku WSDL.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="fe7f7-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="fe7f7-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="fe7f7-146">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe7f7-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe7f7-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-148">Określa, czy obiekt usługi zostanie odtworzony po zakończeniu bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="fe7f7-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="fe7f7-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="fe7f7-150">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe7f7-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe7f7-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-152">Określa, czy oczekujące transakcje są wykonywane po zamknięciu bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="fe7f7-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="fe7f7-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="fe7f7-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7f7-154">Data type: string</span></span>  
  
 <span data-ttu-id="fe7f7-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-156">Określa poziom izolacji transakcji.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="fe7f7-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="fe7f7-157">TransactionTimeout</span></span>  
 <span data-ttu-id="fe7f7-158">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="fe7f7-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="fe7f7-159">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-160">Okres, w którym należy wykonać transakcję.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="fe7f7-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="fe7f7-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="fe7f7-162">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe7f7-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe7f7-163">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-164">Określa, czy umożliwia wybieranie wykonywanie wątków w bieżącym kontekście synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="fe7f7-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="fe7f7-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="fe7f7-166">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe7f7-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe7f7-167">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7f7-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7f7-168">Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe7f7-169">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe7f7-169">Requirements</span></span>  
  
|<span data-ttu-id="fe7f7-170">MOF</span><span class="sxs-lookup"><span data-stu-id="fe7f7-170">MOF</span></span>|<span data-ttu-id="fe7f7-171">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fe7f7-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fe7f7-172">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fe7f7-172">Namespace</span></span>|<span data-ttu-id="fe7f7-173">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fe7f7-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe7f7-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe7f7-174">See also</span></span>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>

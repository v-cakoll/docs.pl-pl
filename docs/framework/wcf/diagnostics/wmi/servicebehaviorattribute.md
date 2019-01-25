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
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="methods"></a>Metody  
 Klasa ServiceBehaviorAttribute nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceBehaviorAttribute ma następujące właściwości:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy należy automatycznie Zamknij sesję, gdy klient zamyka sesję danych wyjściowych.  
  
### <a name="concurrencymode"></a>Właściwość ConcurrencyMode  
 Typ danych: ciąg  
Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.  
  
### <a name="configurationname"></a>ConfigurationName  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa konfiguracji usługi.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy wysyłać dane serializacji nieznany podczas transmisji.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.  
  
### <a name="instancecontextmode"></a>InstanceContextMode  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, kiedy tworzony jest nowy obiekt usługi.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalną liczbę elementów dozwoloną w Zserializowany obiekt.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Atrybut nazwy usługi w języku WSDL.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Docelowy obszar nazw usługi w języku WSDL.  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy obiekt usługi zostanie odtworzony po zakończeniu bieżącej transakcji.  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy oczekujące transakcje są wykonywane po zamknięciu bieżącej sesji.  
  
### <a name="transactionisolationlevel"></a>TransactionIsolationLevel  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Określa poziom izolacji transakcji.  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Okres, w którym należy wykonać transakcję.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy umożliwia wybieranie wykonywanie wątków w bieżącym kontekście synchronizacji.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.ServiceBehaviorAttribute>

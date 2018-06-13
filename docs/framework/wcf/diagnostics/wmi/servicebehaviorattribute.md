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
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="methods"></a>Metody  
 Klasa atrybutu ServiceBehaviorAttribute nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa atrybutu ServiceBehaviorAttribute ma następujące właściwości:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy automatycznie zamykać sesję przy zamykaniu przez klienta sesji wyjściowej.  
  
### <a name="concurrencymode"></a>Właściwość ConcurrencyMode  
 Typ danych: ciąg  
Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy usługa obsługuje jeden wątek, wiele wątków lub wywołania współużytkowane.  
  
### <a name="configurationname"></a>ConfigurationName  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa konfiguracji usługi.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy nieznane dane serializacji serializacji.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy dołączać informacje o zarządzanym wyjątku w informacjach szczegółowych o błędach SOAP zwracanych do klientów na potrzeby debugowania.  
  
### <a name="instancecontextmode"></a>Właściwość InstanceContextMode obiektu  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, kiedy tworzony jest nowy obiekt usługi.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalną liczbę elementów dozwoloną w obiekcie szeregowanym.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Atrybut nazwy usługi w języku WSDL.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Docelowy obszar nazw usługi w języku WSDL.  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy obiekt usługi jest ponownie przetwarzany po zakończeniu bieżącej transakcji.  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy transakcje oczekujące są kończone podczas zamykania bieżącej sesji.  
  
### <a name="transactionisolationlevel"></a>TransactionIsolationLevel  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Określa poziom izolacji transakcji.  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Okres, w ramach którego transakcja musi zostać zakończona.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy używać kontekstu synchronizacji do wybierania kolejności wykonywania wątków.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy system lub aplikacja wymusza przetwarzanie nagłówka MustUnderstand protokołu SOAP.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>

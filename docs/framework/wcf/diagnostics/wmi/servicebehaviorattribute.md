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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7401acd5aefcb7a8c02ea6c05a94374e41d9b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext elementu  
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

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
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="methods"></a>Metody  
 Klasa MsmqBindingElementBase nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa MsmqBindingElementBase ma następujące właściwości:  
  
### <a name="customdeadletterqueue"></a>customDeadLetterQueue  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Identyfikator URI, który zawiera lokalizację kolejki utraconych wiadomości dla każdej aplikacji, gdzie umieszcza komunikaty wygasły lub mają niepowodzeniem transferu lub dostarczania.  
  
### <a name="deadletterqueue"></a>DeadLetterQueue wartość  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość wyliczenia, który wskazuje na typ używanej kolejki utraconych wiadomości.  
  
### <a name="durable"></a>trwałe  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy komunikaty przetwarzane przez to powiązanie są trwałe lub zmienne.  
  
### <a name="exactlyonce"></a>exactlyOnce  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna wskazująca, czy komunikaty przetwarzane przez to powiązanie są odbierane dokładnie raz.  
  
### <a name="maxretrycycles"></a>maxRetryCycles  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna liczba ponownych prób cyklów próby dostarczenia komunikatów do aplikacji odbierającej.  
  
### <a name="receiveerrorhandling"></a>receiveErrorHandling  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawienia obsługi Zarządzanie skażonymi komunikatami.  
  
### <a name="receiveretrycount"></a>receiveRetryCount  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna liczba natychmiastowego ponawiania próby w wiadomości, które są odczytywane z kolejki aplikacji.  
  
### <a name="retrycycledelay"></a>retryCycleDelay  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość wskazująca czas opóźnienia między cykle przy próbie dostarczenia komunikatu, którego nie można dostarczyć natychmiast.  
  
### <a name="timetolive"></a>timeToLive  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Przedział czasu, która wskazuje, jak długo komunikaty przetwarzane przez to powiązanie mogą znajdować się w kolejce, zanim wygasną.  
  
### <a name="usemsmqtracing"></a>useMsmqTracing  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna, która wskazuje, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone.  
  
### <a name="usesourcejournal"></a>useSourceJournal  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna wskazująca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>

---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 9a9d48cc49b19f737236939c83a4e9421013f48f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="msmqbindingelementbase"></a>MsmqBindingElementBase
MsmqBindingElementBase  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
### <a name="customdeadletterqueue"></a>CustomDeadLetterQueue  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator URI zawiera lokalizację kolejki utraconych wiadomości dla każdej aplikacji, gdzie umieścić są komunikaty wygasłe, lub które nie przeszły przesłanie bądź dostarczenie.  
  
### <a name="deadletterqueue"></a>DeadLetterQueue wartość  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość wyliczenia wskazująca typ używanej kolejki utraconych wiadomości.  
  
### <a name="durable"></a>trwałe  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy komunikaty przetwarzane przez to powiązanie są trwałe lub zmienne.  
  
### <a name="exactlyonce"></a>ExactlyOnce  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna wskazująca, czy komunikaty przetwarzane przez to powiązanie są odbierane dokładnie raz.  
  
### <a name="maxretrycycles"></a>MaxRetryCycles  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba cykli ponawiania próby dostarczenia komunikatów do aplikacji odbierającej.  
  
### <a name="receiveerrorhandling"></a>ReceiveErrorHandling  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Ustawienia dotyczące obsługi uszkodzonych komunikatów.  
  
### <a name="receiveretrycount"></a>ReceiveRetryCount  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba natychmiastowego ponawiania prób w przypadku komunikatu odczytywanego z kolejki aplikacji.  
  
### <a name="retrycycledelay"></a>RetryCycleDelay  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość wskazująca zwłokę między kolejnymi próbami dostarczenia komunikatu, którego nie można było dostarczyć natychmiast.  
  
### <a name="timetolive"></a>Wartość TimeToLive  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Przedział czasu, która wskazuje, jak długo komunikaty przetwarzane przez to powiązanie mogą znajdować się w kolejce, zanim wygasną.  
  
### <a name="usemsmqtracing"></a>UseMsmqTracing  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna, która wskazuje, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone.  
  
### <a name="usesourcejournal"></a>UseSourceJournal  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna wskazująca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>

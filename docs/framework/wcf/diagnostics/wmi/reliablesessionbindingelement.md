---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2e2e36486c3788cd714ffd0ed545fbb14f831476
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197044"
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa elementu ReliableSessionBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa elementu ReliableSessionBindingElement ma następujące właściwości:  
  
### <a name="acknowledgementinterval"></a>AcknowledgementInterval  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Interwał czasu miejsca docelowego oczekiwania przed wysłaniem potwierdzenia do źródła wiadomości na niezawodne kanały, które są tworzone przez fabrykę.  
  
### <a name="flowcontrolenabled"></a>FlowControlEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy włączone jest sterowanie przepływem.  
  
### <a name="inactivitytimeout"></a>Limit czasu nieaktywności  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Określa maksymalny czas, przez który kanał umożliwi drugiej strony komunikujące się nie na niewysyłanie komunikatów przed spowodowaniem błędu kanału.  
  
### <a name="maxpendingchannels"></a>MaxPendingChannels  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalną liczbę kanałów oczekujących na odbiornik do zaakceptowania.  
  
### <a name="maxretrycount"></a>MaxRetryCount  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalną liczbę prób niezawodny kanał retransmitować komunikat, którego nie otrzymano potwierdzenia, wywołując `Send` kanału źródłowego.  
  
### <a name="maxtransferwindowsize"></a>MaxTransferWindowSize  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Rozmiar okna maksymalną niezawodnej sesji.  
  
### <a name="ordered"></a>Uporządkowane  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy komunikaty dotrą do celu w kolejności wysłania.  
  
### <a name="reliablemessagingversion"></a>ReliableMessagingVersion  
 Typ danych: liczba całkowita  
  
 Dostęp do typu: tylko do odczytu  
  
 Liczba całkowita, która określa wersję protokołu WS-ReliableMessaging, które są używane w niezawodnej sesji.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>

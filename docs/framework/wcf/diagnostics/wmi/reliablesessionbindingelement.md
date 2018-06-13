---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2f04e6794342d7bd0acd51481efcbeceb04fd459
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486656"
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 Klasa obiektu ReliableSessionBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa obiektu ReliableSessionBindingElement ma następujące właściwości:  
  
### <a name="acknowledgementinterval"></a>AcknowledgementInterval  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Interwał czasu oczekiwania przed wysłaniem potwierdzenia do źródła komunikatu za pośrednictwem niezawodnych kanałów tworzonych przez fabrykę miejsca docelowego.  
  
### <a name="flowcontrolenabled"></a>FlowControlEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy włączone jest sterowanie przepływem.  
  
### <a name="inactivitytimeout"></a>Limit czasu nieaktywności  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Określa maksymalny czas, który będzie kanał zezwoli innemu uczestnikowi komunikacji nie na niewysyłanie komunikatów przed spowodowaniem błędu kanału.  
  
### <a name="maxpendingchannels"></a>MaxPendingChannels  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba kanałów oczekujących na akceptację na odbiornika.  
  
### <a name="maxretrycount"></a>MaxRetryCount  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalną liczbę prób niezawodny kanał ponownego przesłania wiadomości nie otrzymano potwierdzenia, poprzez wywoływanie metody `Send` kanału źródłowego.  
  
### <a name="maxtransferwindowsize"></a>MaxTransferWindowSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny rozmiar okna transmisji dla sesji niezawodnej.  
  
### <a name="ordered"></a>uporządkowane  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy komunikaty dotrą do celu w kolejności wysłania.  
  
### <a name="reliablemessagingversion"></a>ReliableMessagingVersion  
 Typ danych: liczba całkowita  
  
 Dostęp typu: tylko do odczytu  
  
 Liczba całkowita określająca wersja protokołu WS-ReliableMessaging, używanego w niezawodnej sesji.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>

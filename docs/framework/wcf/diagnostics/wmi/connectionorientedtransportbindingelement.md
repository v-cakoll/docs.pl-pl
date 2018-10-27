---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 49f030c05f02280d483ac2a836cbe75716b7b5cc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185057"
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ConnectionOrientedTransportBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ConnectionOrientedTransportBindingElement ma następujące właściwości:  
  
### <a name="channelinitializationtimeout"></a>channelInitializationTimeout  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Timespan określający czas inicjowania kanału musi ukończyć przed przekroczeniem limitu czasu.  
  
### <a name="connectionbuffersize"></a>ConnectionBufferSize  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Rozmiar buforu używany do przesyłania fragmentów serializacji wiadomości na łączu z klienta lub usługi.  
  
### <a name="hostnamecomparisonmode"></a>parametru hostNameComparisonMode  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.  
  
### <a name="maxbuffersize"></a>wartość maxBufferSize  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalny rozmiar buforu do użycia.  
  
### <a name="maxoutputdelay"></a>MaxOutputDelay  
 Typ danych: Data i godzina  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalny interwał czasu, który fragment wiadomości lub cały komunikat może pozostać buforowanych w pamięci przed wysłane.  
  
### <a name="maxpendingaccepts"></a>maxPendingAccepts  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna liczba oczekujących asynchronicznych zaakceptować wątki, które są dostępne do przetwarzania przychodzących połączeń z usługą.  
  
### <a name="maxpendingconnections"></a>maxPendingConnections  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna liczba oczekujących połączeń.  
  
### <a name="transfermode"></a>Tryb transferu  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która określa, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

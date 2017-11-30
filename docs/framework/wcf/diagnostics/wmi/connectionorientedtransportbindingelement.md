---
title: ConnectionOrientedTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d28bedb67850b9bb77c25c8d29c6e39b056770a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
### <a name="channelinitializationtimeout"></a>limitu czasu channelInitializationTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Obiekt timespan określający sposób inicjacji kanału musi zostać ukończona przed przekroczeniem limitu czasu.  
  
### <a name="connectionbuffersize"></a>connectionBufferSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Rozmiar buforu używany do przesyłania fragmentu szeregowanego komunikatu podczas transmisji od klienta lub usługi.  
  
### <a name="hostnamecomparisonmode"></a>parametru hostNameComparisonMode  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.  
  
### <a name="maxbuffersize"></a>wartość maxBufferSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny rozmiar bufora.  
  
### <a name="maxoutputdelay"></a>maxOutputDelay  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny interwał czasu, przez który fragment lub całość komunikatu może pozostawać buforowana w pamięci przed wysłaniem.  
  
### <a name="maxpendingaccepts"></a>maxPendingAccepts  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba oczekujących asynchronicznych wątków dostępnych do przetwarzania przychodzących połączeń z usługą akceptujących.  
  
### <a name="maxpendingconnections"></a>maxPendingConnections  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba oczekujących połączeń.  
  
### <a name="transfermode"></a>Tryb transferu  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która określa, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>

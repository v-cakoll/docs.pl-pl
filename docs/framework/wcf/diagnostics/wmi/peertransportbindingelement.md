---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 193000acf2f3c8a0eddb2552559ee40a0f5fced9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa PeerTransportBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa PeerTransportBindingElement ma następujące właściwości:  
  
### <a name="listenipaddress"></a>ListenIPAddress  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Adres IP, na którym węzeł elementu równorzędnego nasłuchuje wiadomości.  
  
### <a name="port"></a>Port  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Port interfejsu sieciowego, na którym znajduje się ten procesów powiązania elementu równorzędnego kanału wiadomości.  
  
### <a name="security"></a>Zabezpieczenia  
 Typ danych: PeerSecuritySettings  
  
 Dostęp typu: tylko do odczytu  
  
 Ustawienia zabezpieczeń transportu elementów równorzędnych.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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

---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485648"
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

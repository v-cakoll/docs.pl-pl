---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 58bf07b0429ca2435b5aae3683ef69951a10003e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185186"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
### <a name="listenipaddress"></a>listenIPAddress  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Adres IP, na którym węzeł równorzędny będzie nasłuchiwać pod kątem komunikatów.  
  
### <a name="port"></a>Port  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Port interfejsu sieciowego, na którym znajduje się ten kanał wiadomości w komunikacji równorzędnej procesy powiązania.  
  
### <a name="security"></a>Zabezpieczenia  
 Typ danych: PeerSecuritySettings  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawienia zabezpieczeń transport elementu równorzędnego.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

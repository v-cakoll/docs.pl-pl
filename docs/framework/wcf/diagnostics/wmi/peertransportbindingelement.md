---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980438"
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
  
### <a name="listenipaddress"></a>ListenIPAddress  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Adres IP, na którym węzeł równorzędny będzie nasłuchiwać pod kątem komunikatów.  
  
### <a name="port"></a>Port  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Port interfejsu sieciowego, na którym znajduje się ten kanał wiadomości w komunikacji równorzędnej procesy powiązania.  
  
### <a name="security"></a>Zabezpieczenia  
 Typ danych: PeerSecuritySettings  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawienia zabezpieczeń transport elementu równorzędnego.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 04326484bbf1f07c66ad8fb401642880f9ba8c6e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193932"
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa TcpTransportBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa TcpTransportBindingElement ma następujące właściwości:  
  
### <a name="connectionpoolsettings"></a>connectionPoolSettings  
 Typ danych: TcpConnectionPoolSettings  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawienia puli połączeń.  
  
### <a name="listenbacklog"></a>listenBacklog  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna liczba żądań w kolejce połączeń, które może być oczekujące.  
  
### <a name="portsharingenabled"></a>portSharingEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia.  
  
### <a name="teredoenabled"></a>teredoEnabled  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy jest włączony protokół Teredo (technologia adresować klientów znajdujących się za zaporami).  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6d2717bc2d1d14e369af2b9c5a8c0affb67501d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979241"
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
  
### <a name="connectionpoolsettings"></a>ConnectionPoolSettings  
 Typ danych: TcpConnectionPoolSettings  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawienia puli połączeń.  
  
### <a name="listenbacklog"></a>ListenBacklog  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba żądań w kolejce połączeń, które może być oczekujące.  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia.  
  
### <a name="teredoenabled"></a>TeredoEnabled  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość logiczna określająca, czy jest włączony protokół Teredo (technologia adresować klientów znajdujących się za zaporami).  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

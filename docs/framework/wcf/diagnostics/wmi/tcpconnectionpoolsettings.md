---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975356"
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings
TcpConnectionPoolSettings  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa TcpConnectionPoolSettings nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa TcpConnectionPoolSettings ma następujące właściwości:  
  
### <a name="groupname"></a>GroupName  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa grupy puli połączeń używane przez element powiązania.  
  
### <a name="idletimeout"></a>IdleTimeout  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalny czas na ukończenie przed przekroczeniem limitu czasu operacji dzierżawy.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>

---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 4e89dbe35a5232c612555b273c3d771aad42aeb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584808"
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

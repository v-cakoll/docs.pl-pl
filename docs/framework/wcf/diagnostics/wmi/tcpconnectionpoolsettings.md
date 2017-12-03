---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eaec1b7d179810faaba016cfa0c5eb7e6c950ab6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings
TcpConnectionPoolSettings  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
### <a name="groupname"></a>Nazwa grupy  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa grupy puli połączeń używanej przez element powiązania.  
  
### <a name="idletimeout"></a>IdleTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Typ danych: daty i godziny  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny czas na ukończenie przed przekroczeniem limitu czasu operacji dzierżawy.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba połączeń wychodzących dla każdego punktu końcowego.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>

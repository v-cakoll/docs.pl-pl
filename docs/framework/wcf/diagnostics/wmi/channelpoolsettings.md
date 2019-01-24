---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 4a3e45140765f99f4a30b77fc9d02b167601b50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591484"
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings
ChannelPoolSettings  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ChannelPoolSettings nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ChannelPoolSettings ma następujące właściwości:  
  
### <a name="idletimeout"></a>IdleTimeout  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalny czas dzierżawy na zakończenie operacji przed przekroczeniem limitu czasu.  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba wychodzących kanałów dla każdego punktu końcowego.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>

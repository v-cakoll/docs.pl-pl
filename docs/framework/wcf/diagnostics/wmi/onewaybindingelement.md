---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Metody  
 Element OneWayBindingElement klasa nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa element OneWayBindingElement ma następujące właściwości:  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 Typ danych: ChannelPoolSettings  
  
 Dostęp typu: tylko do odczytu  
  
 Ustawienia puli kanałów.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba zaakceptowanych kanałów.  
  
### <a name="packetroutable"></a>PacketRoutable  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy pakiet jest rutowalny.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>

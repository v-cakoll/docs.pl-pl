---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195817"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa element OneWayBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa element OneWayBindingElement ma następujące właściwości:  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 Typ danych: ChannelPoolSettings  
  
 Dostęp do typu: tylko do odczytu  
  
 Ustawienia puli kanału.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 Typ danych: sint32  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalna liczba zaakceptowanych kanałów.  
  
### <a name="packetroutable"></a>PacketRoutable  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość, która wskazuje, czy pakiet jest routing.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>

---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 761ed0e30c6acca8c910c5dc97dfbae46c1f89bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564841"
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa PeerSecuritySettings nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa PeerSecuritySettings ma następujące właściwości:  
  
### <a name="mode"></a>Tryb  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Czy komunikatu i zabezpieczenia na poziomie transportu używanych przez punkty końcowe skonfigurowane dla tego wiązania.  
  
### <a name="transport"></a>Transport  
 Typ danych: PeerTransportSecuritySettings  
  
 Typ dostępu: tylko do odczytu  
  
 Ustawienia zabezpieczeń transportu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.PeerSecuritySettings>

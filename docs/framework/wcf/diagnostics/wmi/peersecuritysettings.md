---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217890"
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

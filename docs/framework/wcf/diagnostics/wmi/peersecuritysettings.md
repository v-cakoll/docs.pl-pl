---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 02cd483f2f7ec5e599b286b672d051a0e8d57940
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="peersecuritysettings"></a>PeerSecuritySettings
PeerSecuritySettings  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy poziom komunikatu i zabezpieczenia na poziomie transportu są używane przez punkt końcowy skonfigurowany dla powiązania.  
  
### <a name="transport"></a>Transportu  
 Typ danych: Obiekt PeerTransportSecuritySettings  
  
 Dostęp typu: tylko do odczytu  
  
 Ustawienia zabezpieczeń transportu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.PeerSecuritySettings>

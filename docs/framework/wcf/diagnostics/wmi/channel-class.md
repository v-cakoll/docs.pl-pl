---
title: Klasa kanału
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="channel-class"></a>Klasa kanału
Kanał  
  
## <a name="syntax"></a>Składnia  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa kanału nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa kanału ma następujące właściwości.  
  
### <a name="localaddress"></a>LocalAddress  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Lokalny punkt końcowy kanału.  
  
### <a name="ref"></a>ref  
 Typ danych: punktu końcowego  
  
 Dostęp typu: tylko do odczytu  
  
 Łączy się z odwołaniem do punktu końcowego kanału.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Zdalny adres skojarzony z kanałem.  
  
### <a name="sessionid"></a>SessionId  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator bieżącej sesji, jeśli istnieje.  
  
### <a name="type"></a>Typ  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Typ kanału.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.ChannelBase>

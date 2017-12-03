---
title: "Klasa kanału"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 93632d6a178c0f58143fc148a0e1eb51be94ed17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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

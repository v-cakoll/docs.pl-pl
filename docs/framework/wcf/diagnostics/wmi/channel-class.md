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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1df634a61cce695fca74fdfe53beea6c0f83d082
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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

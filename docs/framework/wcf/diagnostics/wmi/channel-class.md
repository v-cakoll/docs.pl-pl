---
title: Klasa kanału
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767451"
---
# <a name="channel-class"></a>Klasa kanału
Kanał  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Typ dostępu: tylko do odczytu  
  
 Lokalny punkt końcowy dla kanału.  
  
### <a name="ref"></a>ref  
 Typ danych: Punkt końcowy  
  
 Typ dostępu: tylko do odczytu  
  
 Łączy się z odwołaniem do punktu końcowego kanału.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Zdalny adres skojarzony z kanałem.  
  
### <a name="sessionid"></a>SessionId  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator bieżącej sesji, jeśli istnieje.  
  
### <a name="type"></a>Typ  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Typ kanału.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.ChannelBase>

---
title: '&lt;Wyczyść&gt; elementu connectionmanagement — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5bcd17cfe1f3bd7531453b62552a4907df5b96bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a>&lt;Wyczyść&gt; elementu connectionmanagement — (ustawienia sieciowe)
Usuwa listy zarządzania połączenia.  
  
 \<Konfiguracja >  
\<system.net>  
\<connectionmanagement — >  
\<Wyczyść >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[connectionmanagement —](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostem sieci.|  
  
## <a name="remarks"></a>Uwagi  
 `clear` Element czyści wszystkie wpisy z listy zarządzania połączenia.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje wyczyszczenie listy zarządzania połączenia, a następnie dodaje nowe wpisy zarządzania połączenia www.contoso.com serwera i innych hostów w sieci.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

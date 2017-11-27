---
title: "&lt;Usuń&gt; elementu connectionmanagement — (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 92536ad7605211f3a7f606920b054a217427c8f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a>&lt;Usuń&gt; elementu connectionmanagement — (ustawienia sieciowe)
Usuwa adres IP lub nazwa DNS z listy zarządzania połączenia.  
  
 \<Konfiguracja >  
\<System.NET >  
\<connectionmanagement — >  
\<Usuń >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`address`|Adres IP lub nazwę DNS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[connectionmanagement —](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostem sieci.|  
  
## <a name="remarks"></a>Uwagi  
 `remove` Element usuwa wpis listy zarządzania połączenia dla określonego serwera.  
  
 Wartość `address` atrybutu powinna być prawidłową nazwą adres lub hosta IP.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład usuwa wszystkie pozycje listy zarządzania połączenia dla www.adventure-works.com serwera, a następnie konfiguruje aplikację do korzystania z połączeń cztery www.contoso.com serwera i dwa połączenia do innych serwerów.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

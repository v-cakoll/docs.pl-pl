---
title: <connectionManagement>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154897"
---
# <a name="connectionmanagement-element-network-settings"></a>\<connectionManagement> Element (Ustawienia sieciowe)
Określa maksymalną liczbę połączeń z hostem sieciowym.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a>Składnia  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Dodaj](add-element-for-connectionmanagement-network-settings.md)|Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.|  
|[Wyczyść](clear-element-for-connectionmanagement-network-settings.md)|Czyści listę zarządzania połączeniami.|  
|[Usunąć](remove-element-for-connectionmanagement-network-settings.md)|Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Zawiera ustawienia określające sposób łączenia się programu .NET Framework z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 Element `connectionManagement` definiuje maksymalną liczbę połączeń z serwerem lub grupą serwerów.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguruje aplikację do używania `www.contoso.com` czterech połączeń z serwerem i dwóch połączeń ze wszystkimi innymi serwerami.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schemat ustawień sieci](index.md)

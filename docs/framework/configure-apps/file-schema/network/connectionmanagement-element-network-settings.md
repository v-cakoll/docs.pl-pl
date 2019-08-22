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
ms.openlocfilehash: faaba1b9de302ed916ad1a81c7e80b3fb5a67170
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664166"
---
# <a name="connectionmanagement-element-network-settings"></a>\<connectionManagement >, element (Ustawienia sieci)
Określa maksymalną liczbę połączeń z hostem sieciowym.  
  
 \<> konfiguracji  
\<system.net>  
\<connectionManagement >  
  
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
|[add](add-element-for-connectionmanagement-network-settings.md)|Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.|  
|[Wyczyść](clear-element-for-connectionmanagement-network-settings.md)|Czyści listę zarządzania połączeniami.|  
|[remove](remove-element-for-connectionmanagement-network-settings.md)|Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 `connectionManagement` Element definiuje maksymalną liczbę połączeń z serwerem lub grupą serwerów.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład służy do konfigurowania aplikacji do korzystania z czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schemat ustawień sieci](index.md)

---
title: <add>, element dla connectionManagement (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 19ebbfba477eeba253a7af0742953cc6a4d45a0e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088517"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a>\<dodać elementu > dla connectionManagement (Ustawienia sieci)
Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**

## <a name="syntax"></a>Składnia  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`address`|Ciąg opisujący adres IP lub nazwę DNS.|  
|`maxconnection`|Maksymalna liczba połączeń dozwolonych dla serwera. Jeśli nie zostanie podany, wartość domyślna to 2.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostem sieciowym.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość atrybutu `address` powinna być gwiazdką wskazującą wszystkie połączenia lub ciąg `<schema>://<idn_hostname>[:<port>]`formularza.  
  
 Jeśli identyfikator URI przesłany do dowolnego interfejsu API protokołu HTTP zawiera Unicode, nazwa zostanie przekonwertowane wewnętrznie przy użyciu <xref:System.Uri.DnsSafeHost%2A>, co może zwrócić ciąg punicode (zachowanie zależne od bieżącej konfiguracji IDN).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład służy do konfigurowania aplikacji do używania czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schemat ustawień sieci](index.md)

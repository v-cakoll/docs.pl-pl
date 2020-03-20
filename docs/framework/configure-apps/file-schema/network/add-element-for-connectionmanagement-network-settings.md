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
ms.openlocfilehash: 093b68d31e03094bedefa96a2f2d53eb3d84edf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155014"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a>\<dodaj element> do łączeniaManagement (Ustawienia sieciowe)
Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**

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
|`maxconnection`|Maksymalna liczba połączeń dozwolonych z serwerem. Jeśli nie podano, wartość domyślna to 2.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[connectionManagement (PołączenieManagement)](connectionmanagement-element-network-settings.md)|Określa maksymalną liczbę połączeń z hostem sieciowym.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość atrybutu `address` powinna być gwiazdką wskazującą wszystkie połączenia lub ciągiem formularza `<schema>://<idn_hostname>[:<port>]`.  
  
 Jeśli identyfikator URI przekazany do dowolnych interfejsów API HTTP zawiera Unicode, nazwa zostanie przekonwertowana wewnętrznie przy użyciu, <xref:System.Uri.DnsSafeHost%2A> który może zwrócić ciąg punicode (zachowanie zależne od bieżącej konfiguracji IDN).  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład konfiguruje aplikację do używania `www.contoso.com` czterech połączeń z serwerem i dwóch połączeń ze wszystkimi innymi serwerami.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schemat ustawień sieci](index.md)

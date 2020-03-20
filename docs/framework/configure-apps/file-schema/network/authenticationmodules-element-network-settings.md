---
title: <authenticationModules>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154975"
---
# <a name="authenticationmodules-element-network-settings"></a>\<authenticationModules> Element (Ustawienia sieciowe)
Określa moduły używane do uwierzytelniania żądań sieciowych.  

[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>uwierzytelniania**

## <a name="syntax"></a>Składnia  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Dodaj](add-element-for-authenticationmodules-network-settings.md)|Dodaje moduł uwierzytelniania do aplikacji.|  
|[Wyczyść](clear-element-for-authenticationmodules-network-settings.md)|Czyści wszystkie moduły uwierzytelniania z aplikacji.|  
|[Usunąć](remove-element-for-authenticationmodules-network-settings.md)|Usuwa moduł uwierzytelniania z aplikacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Zawiera ustawienia określające sposób łączenia się programu .NET Framework z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 Element `authenticationModule` określa moduły uwierzytelniania, które przeprowadzają proces uwierzytelniania z serwerem. Moduł uwierzytelniania musi <xref:System.Net.IAuthenticationModule> implementować interfejs.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia moduł uwierzytelniania. Należy zastąpić wartości dla Version i PublicKeyToken z poprawnymi wartościami dla określonego modułu.  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [Schemat ustawień sieci](index.md)

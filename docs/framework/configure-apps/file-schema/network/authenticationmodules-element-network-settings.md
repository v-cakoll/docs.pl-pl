---
title: <authenticationModules> — Element (Ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 1e40ee4a0bb0731c78d27b7ba9994884ef9ff447
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271593"
---
# <a name="authenticationmodules-element-network-settings"></a>\<authenticationModules >, Element (ustawienia sieci)
Określa moduły używane do uwierzytelniania żądań w sieci.  
  
 \<Konfiguracja >  
\<system.net>  
\<authenticationModules>  
  
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
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|Dodaje moduł uwierzytelniania do aplikacji.|  
|[Usuń zaznaczenie](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|Czyści wszystkie moduły uwierzytelniania z aplikacji.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|Usuwa moduł uwierzytelniania z aplikacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 `authenticationModule` Element określa moduły uwierzytelniania, które należy przeprowadzić proces uwierzytelniania z serwerem. Moduł uwierzytelniania musi implementować <xref:System.Net.IAuthenticationModule> interfejsu.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia moduł uwierzytelniania. Należy zastąpić wartości wersji i PublicKeyToken poprawne wartości dla określonego modułu.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

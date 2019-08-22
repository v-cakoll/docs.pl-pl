---
title: <PreferComInsteadOfManagedRemoting>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a71c2b87d0bcb488e4e8fa4de928a103a8e9dabd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663541"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<PreferComInsteadOfManagedRemoting> Element
Określa, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej dla wszystkich wywołań między domenami aplikacji.  
  
 \<> konfiguracji  
\<runtime>  
\<PreferComInsteadOfManagedRemoting>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM zamiast komunikacji zdalnej między granicami domeny aplikacji.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko uruchomieniowe będzie używać komunikacji zdalnej między granicami domeny aplikacji. Domyślnie włączone.|  
|`true`|Środowisko uruchomieniowe będzie używać międzyoperacyjności modelu COM między granicami domeny aplikacji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Po ustawieniu `enabled` atrybutu na `true`, środowisko uruchomieniowe zachowuje się w następujący sposób:  
  
- Środowisko uruchomieniowe nie wywołuje [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , gdy interfejs [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) przechodzi do domeny za pomocą interfejsu com. Zamiast tego konstruuje otokę w [czasie wykonywania](../../../../../docs/standard/native-interop/runtime-callable-wrapper.md) (RCW) wokół obiektu.  
  
- Środowisko uruchomieniowe zwraca E_NOINTERFACE, gdy odbierze `QueryInterface` wywołanie dla interfejsu [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) dla dowolnego otoki (CCW) [modelu COM](../../../../../docs/standard/native-interop/com-callable-wrapper.md) , który został utworzony w tej domenie.  
  
 Te dwa zachowania zapewniają, że wszystkie wywołania przez interfejsy COM między obiektami zarządzanymi między domenami aplikacji korzystają z międzyoperacyjności modelu COM i modelu COM zamiast komunikacji zdalnej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że środowisko uruchomieniowe ma używać międzyoperacyjności modelu COM w granicach izolacji:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)

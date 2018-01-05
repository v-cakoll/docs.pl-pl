---
title: "&lt;appdomainmanagertype —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcfdd9bcd1aa458aad705d4ab129646e746d63b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltappdomainmanagertypegt-element"></a>&lt;appdomainmanagertype —&gt; — Element
Określa typ, który służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji.  
  
 \<Konfiguracja >  
\<Runtime >  
\<appdomainmanagertype — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`value`|Atrybut wymagany. Określa nazwę typu, łącznie z przestrzenią nazw, która służy jako Menedżer domeny aplikacji dla domyślnej domeny aplikacji w procesie.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby określić typ Menedżer domeny aplikacji, należy określić zarówno tego elementu i [ \<appdomainmanagerassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) elementu. Jeśli nie określono żadnego z tych elementów, druga jest ignorowana.  
  
 Po załadowaniu domyślnej domeny aplikacji <xref:System.TypeLoadException> jest generowany, jeśli określony typ nie istnieje w zestawie, który jest określony przez [ \<appdomainmanagerassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) element; i proces zakończy się niepowodzeniem do początek.  
  
 Po określeniu typu Menedżer domeny aplikacji dla domyślnej domeny aplikacji innych domen aplikacji utworzone na podstawie domyślnej domeny aplikacji dziedziczą typ Menedżera domeny aplikacji. Użyj <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> i <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> właściwości, aby określić typ Menedżera domeny w innej aplikacji dla nowej domeny aplikacji.  
  
 Określanie typu Menedżer domeny aplikacji wymaga aplikacja miała pełne zaufanie. (Na przykład aplikacja uruchomiona na komputerze ma pełnego zaufania). Jeśli aplikacja jest w pełni zaufany <xref:System.TypeLoadException> jest generowany.  
  
 Format typu i przestrzeń nazw jest ten sam format, który służy do <xref:System.Type.FullName%2A?displayProperty=nameWithType> właściwości.  
  
 Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określić, że Menedżer domeny aplikacji dla domyślnej domeny aplikacji procesu jest `MyMgr` wpisz `AdMgrExample` zestawu.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [\<appdomainmanagerassembly — > — Element](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [SetAppDomainManagerType, metoda](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)

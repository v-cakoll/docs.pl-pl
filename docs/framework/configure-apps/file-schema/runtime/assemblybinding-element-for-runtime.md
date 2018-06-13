---
title: '&lt;assemblybinding —&gt; elementu &lt;środowiska wykonawczego&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d84c134b8e2b048f39836bbc10af06039e96719e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746179"
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a>&lt;assemblybinding —&gt; elementu &lt;środowiska wykonawczego&gt;
Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.  
  
 \<Konfiguracja >  
\<runtime>  
\<assemblybinding — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Xmlns**|Atrybut wymagany.<br /><br /> Określa przestrzeń nazw XML, wymagane do powiązań zestawów. Należy użyć ciągu "urn: schemas-microsoft-com:asm.v1" jako wartości.|  
|**Element appliesTo**|Określa wersję środowiska uruchomieniowego dotyczy przekierowania zestawu .NET Framework. Ten opcjonalny atrybut używa numeru wersji .NET Framework w celu wskazania dotyczy wersji. Jeśli nie **appliesTo** określono atrybut  **\<assemblybinding — >** element ma zastosowanie do wszystkich wersji platformy .NET Framework. **AppliesTo** atrybutu została wprowadzona w programie .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0. Oznacza to, że wszystkie  **\<assemblybinding — >** elementy są stosowane, gdy przy użyciu platformy .NET Framework w wersji 1.0, nawet jeśli **appliesTo** jest określony atrybut.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Hermetyzuje lokalizacji zasad i zestawu powiązania dla zestawu. Użyj jednej  **\<dependentAssembly >** tagu dla każdego zestawu.|  
|[\<sondowanie >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Określa podkatalogi podczas ładowania zestawów wyszukiwania środowisko uruchomieniowe języka wspólnego.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Określa, czy środowisko wykonawcze ma zastosowanie zasad wydawcy.|  
|[\<qualifyassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Określa pełną nazwę zestawu, które powinny być dynamicznie załadowane, gdy część nazwy jest używany.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do przekierowywania jednej wersji zestawu i podaj codebase.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Poniższy przykład przedstawia użycie **appliesTo** atrybutu przekierowania powiązania zestawu .NET Framework.  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Przekierowywanie wersji zestawu](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)

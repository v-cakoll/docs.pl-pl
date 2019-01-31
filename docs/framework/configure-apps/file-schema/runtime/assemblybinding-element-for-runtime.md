---
title: <assemblyBinding> — Element do <runtime>
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
ms.openlocfilehash: e75f8e0561711fea8646c9da84f1b7553b3f7553
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284404"
---
# <a name="assemblybinding-element-for-runtime"></a>\<assemblybinding — >, Element dla \<runtime >
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
|**xmlns**|Atrybut wymagany.<br /><br /> Określa przestrzeń nazw XML wymagane w celu tworzenia powiązań zestawów. Użyj ciągu "urn: schemas-microsoft-com:asm.v1" jako wartości.|  
|**appliesTo**|Określa wersję środowiska uruchomieniowego, dotyczy przekierowania zestawu .NET Framework. Ten atrybut opcjonalny używa numeru wersji .NET Framework, aby wskazać dla której wersji dotyczy. Jeśli nie **appliesTo** atrybut jest określony,  **\<assemblyBinding >** element ma zastosowanie do wszystkich wersji programu .NET Framework. **AppliesTo** atrybut wprowadzono w programie .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0. Oznacza to, że wszystkie  **\<assemblyBinding >** elementy są stosowane podczas korzystania z wersji programu .NET Framework 1.0, nawet jeśli **appliesTo** atrybut jest określony.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Hermetyzuje powiązania zasad oraz lokalizację zestawu dla zestawu. Użyj jednej  **\<dependentAssembly >** tag dla każdego zestawu.|  
|[\<sondowanie >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Określa podkatalogi podczas ładowania zestawów środowiska uruchomieniowego języka wspólnego wyszukiwania.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Określa, czy środowisko uruchomieniowe mają zastosowanie zasady wydawcy.|  
|[\<qualifyassembly — >](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy część nazwy jest używany.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób przekierowywania wersji zestawu do drugiego i podaj bazę kodu.  
  
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
  
 Poniższy przykład pokazuje, jak używać **appliesTo** atrybutu, aby przekierować powiązanie zestawu .NET Framework.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Przekierowywanie wersji zestawu](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)

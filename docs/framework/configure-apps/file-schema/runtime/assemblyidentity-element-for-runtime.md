---
title: <assemblyIdentity>, element dla <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: 7cce12f6fb4b957d740cd590bd84851fa16a117d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252799"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<assemblyIdentity element > dla \<> środowiska uruchomieniowego
Zawiera informacje identyfikacyjne zestawu.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zestawubinding**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<assemblyIdentity >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Atrybut wymagany.<br /><br /> Nazwa zestawu|  
|`culture`|Atrybut opcjonalny.<br /><br /> Ciąg określający język i kraj/region zestawu.|  
|`publicKeyToken`|Atrybut opcjonalny.<br /><br /> Wartość szesnastkowa, która określa silną nazwę zestawu.|  
|`processorArchitecture`|Atrybut opcjonalny.<br /><br /> Jedna z wartości "x86", "amd64", "MSIL" lub "ia64", określająca architekturę procesora dla zestawu, który zawiera kod specyficzny dla procesora. W wartościach nie jest rozróżniana wielkość liter. Jeśli atrybut jest przypisany dowolną inną wartość, cały `<assemblyIdentity>` element jest ignorowany. Zobacz <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>processorArchitecture — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`amd64`|Tylko architektura AMD x86-64.|  
|`ia64`|Tylko architektura procesorów Intel Itanium.|  
|`msil`|Neutralna w odniesieniu do procesora i bitów na słowo.|  
|`x86`|32-bitowy procesor x86 — natywny lub w środowisku Windows on Windows (WOW) na platformie 64-bitowej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`dependentAssembly`|Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu. Użyj jednego `<dependentAssembly>` elementu dla każdego zestawu.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 **Każde\<elementy > elementu dependentAssembly** muszą mieć jeden  **\<element podrzędny assemblyIdentity >** .  
  
 Jeśli atrybut jest obecny, element ma zastosowanie tylko do zestawu z odpowiednią architekturą procesora. `<assemblyIdentity>` `processorArchitecture` Jeśli atrybut nie istnieje, element może być stosowany do zestawu z dowolną architekturą procesora. `<assemblyIdentity>` `processorArchitecture`  
  
 W poniższym przykładzie przedstawiono plik konfiguracyjny dla dwóch zestawów o tej samej nazwie, który jest przeznaczony dla dwóch różnych architektur procesora, a których wersje nie zostały zachowane w synchronizacji. Gdy aplikacja jest wykonywana na platformie x86, stosuje się `<assemblyIdentity>` pierwszy element, a drugi jest ignorowany. Jeśli aplikacja jest uruchamiana na platformie innej niż x86 lub ia64, obie te wartości są ignorowane.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Jeśli plik konfiguracji zawiera `<assemblyIdentity>` element `processorArchitecture` bez atrybutu i nie zawiera elementu, który jest zgodny z platformą `processorArchitecture` , element bez atrybutu jest używany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak podać informacje o zestawie.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Przekierowywanie wersji zestawu](../../redirect-assembly-versions.md)

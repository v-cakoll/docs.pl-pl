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
ms.openlocfilehash: b026dafbde796bbd8726de56b532ed6710ba2290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154312"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<assemblyIdentity> Element dla \<> środowiska wykonawczego
Zawiera informacje identyfikujące o zestawie.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>montażowy**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyIdentity>**  
  
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
|`publicKeyToken`|Atrybut opcjonalny.<br /><br /> Wartość szesnastkowa określająca silną nazwę zestawu.|  
|`processorArchitecture`|Atrybut opcjonalny.<br /><br /> Jedna z wartości "x86", "amd64", "msil" lub "ia64", określająca architekturę procesora dla zestawu zawierającego kod specyficzny dla procesora. W wartościach nie rozróżnia się wielkość liter. Jeśli atrybut jest przypisany do innych `<assemblyIdentity>` wartości, cały element jest ignorowany. Zobacz: <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>ProcessorArchitecture Attribute processorArchitecture Attribute  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`amd64`|Tylko architektura AMD x86-64.|  
|`ia64`|Tylko architektura Intel Itanium.|  
|`msil`|Neutralny w odniesieniu do procesora i bitów na słowo.|  
|`x86`|32-bitowy procesor x86, natywny lub w środowisku Windows w systemie Windows (WOW) na platformie 64-bitowej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`dependentAssembly`|Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu. Użyj `<dependentAssembly>` jednego elementu dla każdego złożenia.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy ** \<element>>** musi mieć jeden ** \<zestawIdentykość>** element podrzędny.  
  
 Jeśli `processorArchitecture` atrybut jest obecny, `<assemblyIdentity>` element ma zastosowanie tylko do zestawu z odpowiednią architekturą procesora. Jeśli `processorArchitecture` atrybut nie jest obecny, `<assemblyIdentity>` element można zastosować do zestawu z dowolnej architektury procesora.  
  
 W poniższym przykładzie przedstawiono plik konfiguracji dla dwóch zestawów o tej samej nazwie, które są przeznaczone dla dwóch różnych architektur procesora i których wersje nie zostały zachowane w synchronizacji. Gdy aplikacja jest wykonywana na platformie `<assemblyIdentity>` x86, stosuje się pierwszy element, a drugi jest ignorowany. Jeśli aplikacja jest wykonywana na platformie innej niż x86 lub ia64, oba są ignorowane.  
  
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
  
 Jeśli plik konfiguracji `<assemblyIdentity>` zawiera element `processorArchitecture` bez atrybutu i nie zawiera elementu, który pasuje `processorArchitecture` do platformy, element bez atrybutu jest używany.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak podać informacje o zestawie.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Przekierowywanie wersji zestawu](../../redirect-assembly-versions.md)

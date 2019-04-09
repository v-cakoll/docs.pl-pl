---
title: <assemblyIdentity> element dla <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
ms.openlocfilehash: d5766b76f18dce441cb260887a753dcf64642a6f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098705"
---
# <a name="assemblyidentity-element-for-runtime"></a>\<assemblyIdentity >, Element dla \<runtime >
Zawiera informacje identyfikujące zestaw.  
  
 \<Konfiguracja >  
\<runtime>  
\<assemblybinding — >  
\<dependentAssembly>  
\<assemblyIdentity>  
  
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
|`culture`|Atrybut opcjonalny.<br /><br /> Ciąg, który określa język i kraj/region, zestawu.|  
|`publicKeyToken`|Atrybut opcjonalny.<br /><br /> Wartość szesnastkowa, która określa silną nazwę zestawu.|  
|`processorArchitecture`|Atrybut opcjonalny.<br /><br /> Jedna z wartości "x86", "amd64", "msil" lub "ia64", określając architekturę procesora dla zestawu, który zawiera kod specyficzny dla procesora. Wartości nie jest rozróżniana wielkość liter. Jeśli ten atrybut zostanie przypisany jakąkolwiek inną wartość, całą `<assemblyIdentity>` element jest ignorowany. Zobacz <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>Atrybutu processorArchitecture  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`amd64`|AMD tylko architektura x86-64.|  
|`ia64`|Tylko architekturę Intel Itanium.|  
|`msil`|Neutralne pod kątem procesor i bity na słowo.|  
|`x86`|X86 32-bitowy procesor, albo natywne lub Windows w środowisku Windows (WOW) na platformie 64-bitowej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`dependentAssembly`|Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu. Użyj jednej `<dependentAssembly>` elementu dla każdego zestawu.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy  **\<dependentAssembly >** elementu musi mieć jeden  **\<assemblyIdentity >** elementu podrzędnego.  
  
 Jeśli `processorArchitecture` jest obecny, atrybut `<assemblyIdentity>` element ma zastosowanie tylko do zestawu z odpowiedniej architektury procesora. Jeśli `processorArchitecture` nie jest obecny, atrybut `<assemblyIdentity>` elementu można zastosować do zestawu za pomocą dowolnej architektury procesora.  
  
 Poniższy przykład pokazuje plik konfiguracji dla dwóch zestawów o takiej samej nazwie, przeznaczone na platformę dwóch różnych dwóch architektury procesora, a której wersji ma nie została zachowana synchronizację. Gdy aplikacja wykonuje na x86 platformy pierwszy `<assemblyIdentity>` element ma zastosowanie i innych jest ignorowana. Jeśli aplikacja jest wykonywana na platformie innej niż x86 lub ia64, obie są ignorowane.  
  
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
  
 Jeśli plik konfiguracji zawiera `<assemblyIdentity>` element bez `processorArchitecture` atrybutu i nie zawiera element, który odpowiada platformie elementu bez `processorArchitecture` atrybut jest używany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zapewnić informacje o zestawie.  
  
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

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Przekierowywanie wersji zestawu](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)

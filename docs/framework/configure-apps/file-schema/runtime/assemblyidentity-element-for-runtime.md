---
title: '&lt;element assemblyIdentity&gt; elementu &lt;środowiska wykonawczego&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5d985d1620b7dec324c0113bcd5652cede044950
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a>&lt;element assemblyIdentity&gt; elementu &lt;środowiska wykonawczego&gt;
Zawiera informacje identyfikujące zestaw.  
  
 \<Konfiguracja >  
\<runtime>  
\<assemblybinding — >  
\<dependentAssembly >  
\<element assemblyIdentity >  
  
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
|`culture`|Atrybut opcjonalny.<br /><br /> Ciąg, który określa język i kraj/region zestawu.|  
|`publicKeyToken`|Atrybut opcjonalny.<br /><br /> Wartość szesnastkowa, która określa silnej nazwy zestawu.|  
|`processorArchitecture`|Atrybut opcjonalny.<br /><br /> Jedna z wartości "x86", "amd64", "msil" lub "ia64", określający architektury procesora dla zestawu, który zawiera kod specyficznych dla procesora. Wartości nie jest rozróżniana. Jeśli ten atrybut jest przypisany wszelkie inne wartości, całą `<assemblyIdentity>` element jest ignorowana. Zobacz <xref:System.Reflection.ProcessorArchitecture>.|  
  
## <a name="processorarchitecture-attribute"></a>Element processorArchitecture atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`amd64`|64-bitowy procesor AMD tylko.|  
|`ia64`|64-bitowy procesor Intel tylko.|  
|`msil`|Neutralna względem procesora i usługi bits dla programu word|  
|`x86`|32-bitowy procesor Intel, albo natywne lub w systemie Windows w środowisku Windows (WOW) w 64-bitowej platformy.|  
  
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
 Każdy  **\<dependentAssembly >** element musi mieć jeden  **\<assemblyIdentity >** element podrzędny.  
  
 Jeśli `processorArchitecture` jest obecny, atrybut `<assemblyIdentity>` element ma zastosowanie tylko do zestawu z odpowiedniej architektury procesora. Jeśli `processorArchitecture` atrybut nie jest obecny, `<assemblyIdentity>` elementu można zastosować do zestawu z dowolnej architektury procesora.  
  
 W poniższym przykładzie przedstawiono plik konfiguracji dla dwóch zestawów o takiej samej nazwie, która docelowa dwie różne architektury procesora dwóch i których wersje ma nie została zachowana zsynchronizowany. Gdy aplikacja wykonuje na x86 platformy pierwszy `<assemblyIdentity>` element ma zastosowanie i innych jest ignorowana. Jeśli aplikacja jest wykonywana na platformie niż x86 lub ia64, obie są ignorowane.  
  
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
  
 Jeśli plik konfiguracji zawiera `<assemblyIdentity>` elementu bez `processorArchitecture` atrybutu, a nie zawiera element, który odpowiada platformie elementu bez `processorArchitecture` atrybut jest używany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak o podanie informacji o zestawie.  
  
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
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Przekierowywanie wersji zestawu](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)

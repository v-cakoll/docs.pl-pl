---
title: <assemblyBinding>, element dla <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154325"
---
# <a name="assemblybinding-element-for-runtime"></a>\<assemblyBinding>, element dla \<runtime>
Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assemblyBinding>**  
  
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
|**'xmlns**|Atrybut wymagany.<br /><br /> Określa przestrzeń nazw XML wymaganą dla powiązania zestawu. Użyj ciągu "urn: schematys-Microsoft-com: ASM. v1" jako wartości.|  
|**Zignorowan**|Określa wersję środowiska uruchomieniowego, do której odnosi się przekierowanie zestawu .NET Framework. Ten opcjonalny atrybut używa numeru wersji .NET Framework, aby wskazać, której wersji dotyczy. Jeśli nie określono atrybutu **AppliesTo** , **\<assemblyBinding>** element ma zastosowanie do wszystkich wersji .NET Framework. Atrybut **AppliesTo** został wprowadzony w .NET Framework w wersji 1,1; jest on ignorowany przez .NET Framework w wersji 1,0. Oznacza to, że wszystkie **\<assemblyBinding>** elementy są stosowane w przypadku używania .NET Framework w wersji 1,0, nawet jeśli określono atrybut **AppliesTo** .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dependentAssembly>](dependentassembly-element.md)|Hermetyzuje zasady powiązań i lokalizację zestawu. Użyj jednego **\<dependentAssembly>** tagu dla każdego zestawu.|  
|[\<probing>](probing-element.md)|Określa podkatalogi przeszukiwania środowiska uruchomieniowego języka wspólnego podczas ładowania zestawów.|  
|[\<publisherPolicy>](publisherpolicy-element.md)|Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy.|  
|[\<qualifyAssembly>](qualifyassembly-element.md)|Określa pełną nazwę zestawu, który ma być dynamicznie ładowany, gdy zostanie użyta nazwa częściowa.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przekierować jedną wersję zestawu do innej i podać bazę kodu.  
  
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
  
 Poniższy przykład pokazuje, jak używać atrybutu **AppliesTo** do przekierowywania powiązań zestawu .NET Framework.  
  
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

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Przekierowywanie wersji zestawu](../../redirect-assembly-versions.md)

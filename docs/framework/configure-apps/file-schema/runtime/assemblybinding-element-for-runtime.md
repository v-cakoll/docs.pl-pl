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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154325"
---
# <a name="assemblybinding-element-for-runtime"></a>\<element> w \<czasie wykonywania>
Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>montażowy**  
  
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
|**Xmlns**|Atrybut wymagany.<br /><br /> Określa obszar nazw XML wymagany dla powiązania zestawu. Użyj ciągu "urn:schemas-microsoft-com:asm.v1" jako wartości.|  
|**Appliesto**|Określa wersję środowiska uruchomieniowego, do na które ma zastosowanie przekierowanie zestawu .NET Framework. Ten atrybut opcjonalny używa numeru wersji programu .NET Framework, aby wskazać, jakiej wersji dotyczy. Jeśli nie **appliesTo** atrybut jest określony, ** \<assemblyBinding>** element ma zastosowanie do wszystkich wersji programu .NET Framework. Atrybut **appliesTo** został wprowadzony w wersji .NET Framework w wersji 1.1; jest ignorowana przez program .NET Framework w wersji 1.0. Oznacza to, ** \<** że wszystkie elementy>wiązania zestawu są stosowane podczas korzystania z programu .NET Framework w wersji 1.0, nawet jeśli atrybut **appliesTo** jest określony.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>](dependentassembly-element.md)|Hermetyzuje zasady wiązania i lokalizację zestawu dla zestawu. Użyj jednego ** \<zależnegoAsześci>** znacznik dla każdego zestawu.|  
|[\<sondowanie>](probing-element.md)|Określa podkatalogi wyszukiwania środowiska uruchomieniowego języka wspólnego podczas ładowania zestawów.|  
|[\<wydawcaPolicja>](publisherpolicy-element.md)|Określa, czy środowisko wykonawcze stosuje zasady wydawcy.|  
|[\<kwalifikacje>](qualifyassembly-element.md)|Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy używana jest nazwa częściowa.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak przekierować jedną wersję zestawu do innej i podać bazę kodu.  
  
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
  
 W poniższym przykładzie pokazano, jak użyć **atrybutu appliesTo,** aby przekierować powiązanie zestawu .NET Framework.  
  
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

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Przekierowywanie wersji zestawu](../../redirect-assembly-versions.md)

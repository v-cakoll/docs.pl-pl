---
title: <dependentAssembly>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bf1a15ff27f4390f1985a2d2730b1acfcaab2c1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663830"
---
# <a name="dependentassembly-element"></a>\<Elementy > dependentAssembly
Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu. Użyj jednego `dependentAssembly` elementu dla każdego zestawu.  
  
 \<> konfiguracji  
\<runtime>  
\<> zestawubinding  
\<> dependentAssembly  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyIdentity`|Zawiera informacje identyfikacyjne zestawu. Ten element musi być uwzględniony w `dependentAssembly` każdym elemencie.|  
|`codeBase`|Określa, gdzie środowisko uruchomieniowe może znaleźć zestaw współużytkowany, jeśli nie jest zainstalowany na komputerze.|  
|`bindingRedirect`|Przekierowuje jedną wersję zestawu do innej.|  
|`publisherPolicy`|Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy dla tego zestawu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak hermetyzować informacje o zestawie dla dwóch zestawów.  
  
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
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Przekierowywanie wersji zestawu](../../redirect-assembly-versions.md)

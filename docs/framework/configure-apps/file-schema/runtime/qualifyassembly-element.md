---
title: '&lt;qualifyassembly —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbee999feba5839e66f8eb8c0faaa6e90ca85bd5
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613326"
---
# <a name="ltqualifyassemblygt-element"></a>&lt;qualifyassembly —&gt; — Element
Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy część nazwy jest używany.  
  
 \<Konfiguracja >  
\<runtime>  
\<assemblybinding — >  
\<qualifyassembly — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`partialName`|Atrybut wymagany.<br /><br /> Określa nazwę częściowego zestawu, wyświetlaną w kodzie.|  
|`fullName`|Atrybut wymagany.<br /><br /> Określa pełną nazwę zestawu, która jest wyświetlana w globalnej pamięci podręcznej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Wywoływanie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody przy użyciu nazwy zestawów częściowego powoduje, że środowisko uruchomieniowe języka wspólnego do wyszukania zestawu tylko w katalogu podstawowego aplikacji. Użyj  **\<qualifyassembly — >** elementu w pliku konfiguracyjnym aplikacji do udostępniania informacji pełnego zestawu (nazwa, wersja, token klucza publicznego i kultury) i spowodować, że środowisko uruchomieniowe języka wspólnego do wyszukiwania dla zestawu w globalnej pamięci podręcznej.  
  
 **Imię i nazwisko** atrybutu musi zawierać cztery pola tożsamości zestawu: nazwa, wersja, token klucza publicznego i kultury. **PartialName** atrybut częściowo musi odwoływać się do zestawu. Należy określić co najmniej nazwę tekstu zestawu (najbardziej typowe wielkości liter), ale może również obejmować wersji, token klucza publicznego lub kultury (lub dowolnej kombinacji cztery, ale nie wszystkie cztery). **PartialName** musi pasować do nazwy określonej w swojej rozmowy. Na przykład nie można określić `"math"` jako **partialName** atrybutu w pliku konfiguracji i wywołania `Assembly.Load("math, Version=3.3.3.3")` w kodzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wyłącza logicznie wywołanie `Assembly.Load("math")` do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"   
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [NIB: Częściowe odwołania do zestawów](https://msdn.microsoft.com/library/ec90f07a-398c-4306-9401-0fc5ff9cb59f)

---
title: <qualifyAssembly> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 17cfe9fc39d65f146beef5d02c701f5e3e2fbbe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115783"
---
# <a name="qualifyassembly-element"></a>\<element > qualifyAssembly
Określa pełną nazwę zestawu, który ma być dynamicznie ładowany, gdy zostanie użyta nazwa częściowa.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zestawubinding**](assemblybinding-element-for-runtime.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<qualifyAssembly >**  
  
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
|`partialName`|Atrybut wymagany.<br /><br /> Określa częściową nazwę zestawu, która pojawia się w kodzie.|  
|`fullName`|Atrybut wymagany.<br /><br /> Określa pełną nazwę zestawu, która pojawia się w globalnej pamięci podręcznej zestawów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przy użyciu częściowych nazw zestawów powoduje, że środowisko uruchomieniowe języka wspólnego szuka zestawu tylko w katalogu podstawowym aplikacji. Użyj **\<qualifyAssembly >** elementu w pliku konfiguracyjnym aplikacji, aby podać pełne informacje o zestawie (nazwę, wersję, token klucza publicznego i kulturę) i spowodować, że środowisko uruchomieniowe języka wspólnego wyszukuje zestaw w globalnej pamięć podręczna zestawów.  
  
 Atrybut **FullName** musi zawierać cztery pola tożsamości zestawu: nazwę, wersję, token klucza publicznego i kulturę. Atrybut **częściname** musi częściowo odwoływać się do zestawu. Należy określić co najmniej nazwę tekstu zestawu (najbardziej typowe), ale można również dołączyć wersję, token klucza publicznego lub kulturę (lub dowolną kombinację czterech, ale nie wszystkie cztery). **Część częściowa** musi być zgodna z nazwą określoną w wywołaniu. Nie można na przykład określić `"math"` jako atrybutu **częściowego** w pliku konfiguracji i wywołać `Assembly.Load("math, Version=3.3.3.3")` w kodzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład logicznie włącza `Assembly.Load("math")` wywołań do `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Odwołania do zestawów częściowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))

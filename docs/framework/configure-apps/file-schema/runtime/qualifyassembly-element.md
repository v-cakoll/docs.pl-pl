---
title: <qualifyAssembly>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153922"
---
# <a name="qualifyassembly-element"></a>\<qualifyAssembly> Element
Określa pełną nazwę zestawu, który powinien być dynamicznie ładowany, gdy używana jest nazwa częściowa.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>montażowy**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<kwalifikacje>**  
  
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
|`partialName`|Atrybut wymagany.<br /><br /> Określa częściową nazwę zestawu, jak pojawia się w kodzie.|  
|`fullName`|Atrybut wymagany.<br /><br /> Określa pełną nazwę zestawu, jak pojawia się w globalnej pamięci podręcznej zestawów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody przy użyciu nazw zestawu częściowego powoduje, że środowisko uruchomieniowe języka wspólnego wyszukać zestaw tylko w katalogu podstawowym aplikacji. Użyj ** \<elementu qualifyAssembly>** w pliku konfiguracji aplikacji, aby podać pełne informacje o zestawie (nazwa, wersja, token klucza publicznego i kultury) i spowodować, że środowisko uruchomieniowe języka wspólnego do wyszukiwania zestawu w globalnej pamięci podręcznej zestawu.  
  
 Atrybut **fullName** musi zawierać cztery pola tożsamości zestawu: nazwa, wersja, token klucza publicznego i kultury. Atrybut **partialName** musi częściowo odwoływać się do zestawu. Należy określić co najmniej nazwę tekstową zestawu (najczęstszym przypadkiem), ale można również dołączyć wersję, token klucza publicznego lub kultury (lub dowolną kombinację czterech, ale nie wszystkie cztery). **PartialName** musi odpowiadać nazwie określonej w wywołaniu. Na przykład nie `"math"` można określić jako atrybut **partialName** `Assembly.Load("math, Version=3.3.3.3")` w pliku konfiguracji i wywołać w kodzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład logicznie `Assembly.Load("math")` zamienia `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`wywołanie w .  
  
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

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Odwołania do złożenia częściowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))

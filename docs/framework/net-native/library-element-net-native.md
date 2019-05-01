---
title: <Library> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda4f8d3819af05b022e0633d6883cca940f67e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866864"
---
# <a name="library-element-net-native"></a>\<Biblioteka > (architektura .NET Native)
Definiuje zestaw, który zawiera typy i składowe typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.  
  
 \<Dyrektywy > Element  
\<Biblioteka > Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Atrybut wymagany. Określa nazwę zestawu. Elementy podrzędne tego `<Library>` element zdefiniowania zasad odbicia środowiska uruchomieniowego dla typów i składowych typu, w tym zestawie.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*assembly_name*|Prosta nazwa zestawu, bez jego rozszerzenia pliku. Ten atrybut odnosi się do <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości. Na przykład nazwę zestawu o nazwie Extensions.dll jest "Rozszerzenia". Zobacz sekcję Spostrzeżenia, aby specjalną postać *assembly_name* , która obsługuje dołączenie warunkowe metadanych z zestawu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Stosuje zasady do wszystkich typów w określonym zestawie.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Stosuje zasady do wszystkich typów w określonej przestrzeni nazw.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje zasady do określonego typu, takie jak klasy lub struktury.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego typu ogólnego. Na przykład [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element może służyć do definiowania zasad dla `List<String>` typu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md)|Element główny plik dyrektywy środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 [ \<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) element może zawierać zero, co najmniej jeden `<Library>` elementów.  
  
 `<Library>` Element służy jako kontener służący do definiowania elementów programu, w których metadanych jest potrzebnych w czasie wykonywania; ten element nie express zasad. W czasie kompilacji narzędzia kompilatora wyszukiwanie tylko w bibliotece, które są oznaczane `<Library>` element dla elementów programu identyfikowane przez jego elementy podrzędne. Z kolei narzędzia kompilatora Wyszukaj wszystkie biblioteki, w tym.NET Framework podstawowe biblioteki dla elementów programu identyfikowane przez elementy podrzędne [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu.  
  
 `<Library>` dyrektywy może być wykorzystywane w warunkowo. Jeśli nazwa `<Library>` element rozpoczynający się i kończący znak gwiazdki (\*), `<Library>` dyrektywy obowiązuje tylko wtedy, gdy zestaw określony w zakresie od gwiazdki odwołuje się do aplikacji. Na przykład następująca dyrektywa środowisko uruchomieniowe ma zastosowanie tylko wtedy, gdy zestaw Utillities.dll odwołuje się do aplikacji.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<Aplikacja > Element](../../../docs/framework/net-native/application-element-net-native.md)
- [\<Dyrektywy > Element](../../../docs/framework/net-native/directives-element-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)

---
title: Element <Library> (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128370"
---
# <a name="library-element-net-native"></a>Element > biblioteki \<(.NET Native)
Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania.  
  
 Dyrektywy \<> element  
\<Biblioteka > element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Atrybut wymagany. Określa nazwę zestawu. Elementy podrzędne tego elementu `<Library>` definiują zasady odbicia środowiska uruchomieniowego dla typów i elementów członkowskich typu znalezionych w tym zestawie.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*assembly_name*|Prosta nazwa zestawu bez rozszerzenia pliku. Ten atrybut odpowiada właściwości <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>. Na przykład nazwa zestawu o nazwie Extensions. dll ma wartość "Extensions". Zobacz sekcję Uwagi, aby uzyskać specjalną postać *assembly_name* , która obsługuje warunkowe dołączanie metadanych z zestawu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zestawu >](assembly-element-net-native.md)|Stosuje zasady do wszystkich typów w określonym zestawie.|  
|[\<przestrzeni nazw >](namespace-element-net-native.md)|Stosuje zasady do wszystkich typów w konkretnym obszarze nazw.|  
|[Typ\<](type-element-net-native.md)|Stosuje zasady do określonego typu, na przykład klasy lub struktury.|  
|[\<TypeInstantiation >](typeinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego typu ogólnego. Na przykład element [\<TypeInstantiation >](typeinstantiation-element-net-native.md) może służyć do definiowania zasad dla typu `List<String>`.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Dyrektywy \<](directives-element-net-native.md)|Element główny pliku dyrektywy środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 [Dyrektywy\<](directives-element-net-native.md) element może zawierać zero, jeden lub więcej elementów `<Library>`.  
  
 Element `<Library>` służy jako kontener do definiowania elementów programu, których metadane są konieczne w czasie wykonywania; Ten element nie ma zasad ekspresowych. W czasie kompilacji narzędzia kompilatora przeszukują tylko bibliotekę wyznaczony przez element `<Library>` dla elementów programu identyfikowanych przez jego elementy podrzędne. W przeciwieństwie do narzędzi kompilatora przeszukiwane są wszystkie biblioteki, including.NET Framework Core librarys dla elementów programu identyfikowanych przez elementy podrzędne elementu [> aplikacji\<](application-element-net-native.md) .  
  
 dyrektywy `<Library>` mogą być stosowane warunkowo. Jeśli nazwa elementu `<Library>` rozpoczyna się i kończy się gwiazdką (\*), dyrektywa `<Library>` ma wpływ tylko wtedy, gdy zestaw określony między gwiazdkami jest przywoływany przez aplikację. Na przykład następująca dyrektywa środowiska uruchomieniowego ma zastosowanie tylko wtedy, gdy aplikacja jest przywoływana przez zestaw Utilities. dll.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<> elementu aplikacji](application-element-net-native.md)
- [Dyrektywy \<> element](directives-element-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)

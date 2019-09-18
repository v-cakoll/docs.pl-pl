---
title: <Library>— Element (.NET Native)
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc3c85ab99574c96d8a68d4221f218a1340e4122
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049651"
---
# <a name="library-element-net-native"></a>\<Biblioteka > element (.NET Native)
Definiuje zestaw zawierający typy i elementy członkowskie typu, których metadane są dostępne do odbicia w czasie wykonywania.  
  
 \<Dyrektywy > element  
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
|`Name`|Atrybut wymagany. Określa nazwę zestawu. Elementy podrzędne tego `<Library>` elementu definiują zasady odbicia środowiska uruchomieniowego dla typów i elementów członkowskich typu znalezionych w tym zestawie.|  
  
## <a name="name-attribute"></a>Atrybut nazwy  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*assembly_name*|Prosta nazwa zestawu bez rozszerzenia pliku. Ten atrybut odpowiada <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości. Na przykład nazwa zestawu o nazwie Extensions. dll ma wartość "Extensions". Zobacz sekcję Uwagi, aby uzyskać specjalną postać *assembly_name* , która obsługuje warunkowe dołączanie metadanych z zestawu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> Zestawu](assembly-element-net-native.md)|Stosuje zasady do wszystkich typów w określonym zestawie.|  
|[\<Namespace>](namespace-element-net-native.md)|Stosuje zasady do wszystkich typów w konkretnym obszarze nazw.|  
|[\<Type>](type-element-net-native.md)|Stosuje zasady do określonego typu, na przykład klasy lub struktury.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego typu ogólnego. Na przykład [ \<element TypeInstantiation >](typeinstantiation-element-net-native.md) może służyć do `List<String>` definiowania zasad dla typu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dyrektywy >](directives-element-net-native.md)|Element główny pliku dyrektywy środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 Dyrektywy > element może zawierać zero, jeden lub więcej `<Library>` elementów. [ \<](directives-element-net-native.md)  
  
 `<Library>` Element służy jako kontener do definiowania elementów programu, których metadane są konieczne w czasie wykonywania; ten element nie ma zasad ekspresowych. W czasie kompilacji narzędzia kompilatora przeszukują tylko bibliotekę wyznaczony przez `<Library>` element dla elementów programu identyfikowanych przez jego elementy podrzędne. Z kolei narzędzia kompilatora przeszukują wszystkie biblioteki, including.NET Framework Core librarys dla elementów programu identyfikowanych przez elementy [ \<podrzędne aplikacji >](application-element-net-native.md) elementu.  
  
 `<Library>`dyrektywy mogą być warunkowo wykorzystywane. Jeśli nazwa `<Library>` elementu zaczyna się i kończy się gwiazdką (\*), `<Library>` dyrektywa ma wpływ tylko wtedy, gdy zestaw określony między gwiazdkami jest przywoływany przez aplikację. Na przykład następująca dyrektywa środowiska uruchomieniowego ma zastosowanie tylko wtedy, gdy aplikacja jest przywoływana przez zestaw Utilities. dll.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<Element > aplikacji](application-element-net-native.md)
- [\<Dyrektywy > element](directives-element-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)

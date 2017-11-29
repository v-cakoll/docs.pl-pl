---
title: Element &lt;Library&gt; (architektura .NET Native)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b93335d0d5d1524c9a0b955d1ea279be8c0f243
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlibrarygt-element-net-native"></a>Element &lt;Library&gt; (architektura .NET Native)
Definiuje zestaw zawierający typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania.  
  
 \<Dyrektywy > — Element  
\<Biblioteka > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Name`|Atrybut wymagany. Określa nazwę zestawu. Elementy podrzędne tego `<Library>` element zdefiniowania zasad środowiska uruchomieniowego odbicia dla typów i członków typu w tym zestawie.|  
  
## <a name="name-attribute"></a>Nazwa atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*nazwa_zestawu*|Prosta nazwa zestawu, bez jego rozszerzenie pliku. Ten atrybut odpowiada <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> właściwości. Na przykład nazwa zestawu o nazwie Extensions.dll jest "Rozszerzenia". Specjalna forma w sekcji uwag *nazwa_zestawu* obsługującej dołączenie warunkowe metadanych z zestawu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)|Stosuje zasady do wszystkich typów w określonym zestawie.|  
|[\<Namespace >](../../../docs/framework/net-native/namespace-element-net-native.md)|Stosuje zasady do wszystkich typów w określonej przestrzeni nazw.|  
|[\<Typ >](../../../docs/framework/net-native/type-element-net-native.md)|Stosuje zasady do określonego typu, takich jak klasy lub struktury.|  
|[\<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Stosuje zasady do skonstruowanego typu ogólnego. Na przykład [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element może służyć do zdefiniowania zasad dla `List<String>` typu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md)|Element główny pliku dyrektyw środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 [ \<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) element może zawierać zero, co najmniej jeden `<Library>` elementów.  
  
 `<Library>` Elementu służy jako kontener do zdefiniowania elementów program, którego metadanych jest wymagane w czasie wykonywania; ten element nie wyrażenie zasad. W czasie kompilacji narzędzia kompilatora wyszukiwania biblioteki wskazywany przez `<Library>` elementu dla elementów programu identyfikowane przez jego elementy podrzędne. Z kolei narzędzia kompilatora wyszukiwać wszystkie biblioteki, including.NET Framework core bibliotek, określone przez elementy podrzędne elementy programu [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu.  
  
 `<Library>`dyrektywy mogą zostać użyte warunkowo. Jeśli nazwa `<Library>` elementu rozpoczyna się i kończy się gwiazdką (*), `<Library>` dyrektywy przynosi efekty tylko wtedy, gdy odwołuje się do zestawu określonego między gwiazdki przez aplikację. Na przykład następujące dyrektyw środowiska uruchomieniowego ma zastosowanie tylko wtedy, gdy odwołuje się do zestawu Utillities.dll przez aplikację.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<Aplikacja > — Element](../../../docs/framework/net-native/application-element-net-native.md)  
 [\<Dyrektywy > — Element](../../../docs/framework/net-native/directives-element-net-native.md)  
 [Odwołanie do pliku konfiguracji dyrektyw (rd.xml) środowiska wykonawczego](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)

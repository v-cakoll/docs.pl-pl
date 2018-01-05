---
title: "Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f452a32b209c30175f95aec7a8a90e0783c10086
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)
Dyrektyw środowiska uruchomieniowego (. rd.xml) pliku jest plik konfiguracyjny XML, który określa, czy program wyznaczonych elementy są dostępne w celu odbicia. Oto przykład pliku dyrektyw środowiska uruchomieniowego:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
<Application>  
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />  
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />  
  
  <Namespace Name="System.Collections.ObjectModel" >  
    <TypeInstantiation Name="ObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />  
    <TypeInstantiation Name="ReadOnlyObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />  
  </Namespace>  
</Application>  
</Directives>  
```  
  
## <a name="the-structure-of-a-runtime-directives-file"></a>Struktura pliku dyrektyw środowiska uruchomieniowego  
 Używa pliku dyrektyw środowiska uruchomieniowego `http://schemas.microsoft.com/netfx/2013/01/metadata` przestrzeni nazw.  
  
 Element główny jest [dyrektywy](../../../docs/framework/net-native/directives-element-net-native.md) elementu. Może zawierać zero lub więcej [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) elementów i zero lub jeden [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) element, jak pokazano w następującej struktury. Atrybuty [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) element można definiować całej aplikacji w czasie wykonywania odbicia zasad lub może służyć jako kontener dla elementów podrzędnych. [Biblioteki](../../../docs/framework/net-native/library-element-net-native.md) element, z drugiej strony, to po prostu kontener. Elementy podrzędne [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) i [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) elementy Definiowanie typów, metod, pola, właściwości i zdarzenia, które są dostępne w celu odbicia.  
  
 Aby uzyskać informacje, wybierz elementy z następującej struktury, lub zobacz [elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md). W następujących hierarchii wielokropka oznacza strukturze cyklicznej. Informacje w nawiasach wskazują, czy ten element jest opcjonalne lub wymagane, a jeśli jest używana, liczbę wystąpień (jeden lub wiele) są dozwolone.  
  
 [Dyrektywy](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]  
 [Aplikacja](../../../docs/framework/net-native/application-element-net-native.md) [0:1]  
 [Zestaw](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 . . .  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 [Podtypów](../../../docs/framework/net-native/subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1]  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 . . .  
 [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (typ zawierający jest atrybut) [O:1]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [Parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]  
 [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (skonstruowany Metoda ogólna) [0:M]  
 [Właściwość](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Zdarzenie](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 . . .  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [Parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]  
 [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (skonstruowany Metoda ogólna) [0:M]  
 [Właściwość](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Zdarzenie](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [Biblioteka](../../../docs/framework/net-native/library-element-net-native.md) [0:M]  
 [Zestaw](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 . . .  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 . . .  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 [Podtypów](../../../docs/framework/net-native/subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1]  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 . . .  
 [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (typ zawierający jest atrybut) [O:1]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (skonstruowany Metoda ogólna) [0:M]  
 [Właściwość](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Zdarzenie](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 [Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 . . .  
 [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruować typu ogólnego) [0:M]  
 . . .  
 [Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (skonstruowany Metoda ogólna) [0:M]  
 [Właściwość](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Zdarzenie](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
  
 [Aplikacji](../../../docs/framework/net-native/application-element-net-native.md) element może mieć żadnych atrybutów lub może być atrybutów zasad omówione w [sekcji dyrektywy i zasad środowiska uruchomieniowego](#Directives).  
  
 A [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) element ma jeden atrybut `Name`, który określa nazwę biblioteki lub zestawu bez rozszerzenie pliku. Na przykład następująca [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) element ma zastosowanie do zestawu o nazwie Extensions.dll.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <!-- Child elements go here -->    
  </Application>  
  <Library Name="Extensions">  
     <!-- Child elements go here -->    
  </Library>  
</Directives>  
```  
  
<a name="Directives"></a>   
## <a name="runtime-directives-and-policy"></a>Dyrektyw środowiska uruchomieniowego i zasady  
 [Aplikacji](../../../docs/framework/net-native/application-element-net-native.md) sam element i elementy podrzędne [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) i [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) elementy wyrażenie zasad; oznacza to, definiują sposób, w którym można zastosować aplikacji odbicie do elementu programu. Typ zasad jest określany przez atrybut elementu (na przykład `Serialize`). Wartość zasad jest definiowana przez wartość atrybutu (na przykład `Serialize="Required"`).  
  
 Wszystkie zasady określony przez atrybut elementu dotyczy wszystkie elementy podrzędne, które nie określają wartość dla tej zasady. Na przykład, jeśli określono zasady za pomocą [typu](../../../docs/framework/net-native/type-element-net-native.md) element, który zasady stosowane do wszystkich zawartych w niej typy i elementy członkowskie, dla których zasady nie jest jawnie określony.  
  
 Zasady, które można wyrazić za [aplikacji](../../../docs/framework/net-native/application-element-net-native.md), [zestawu](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Podtypów](../../../docs/framework/net-native/subtypes-element-net-native.md), i [typu](../../../docs/framework/net-native/type-element-net-native.md) elementy różni się od zasad, który może zostać wyrażona dla indywidualnych elementów członkowskich (przez [metody](../../../docs/framework/net-native/method-element-net-native.md), [właściwości](../../../docs/framework/net-native/property-element-net-native.md), [Pola](../../../docs/framework/net-native/field-element-net-native.md), i [zdarzeń](../../../docs/framework/net-native/event-element-net-native.md) elementów).  
  
### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Określanie zasad dla zestawów, obszary nazw i typy  
 [Aplikacji](../../../docs/framework/net-native/application-element-net-native.md), [zestawu](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [podtypów](../../../docs/framework/net-native/subtypes-element-net-native.md)i [ Typ](../../../docs/framework/net-native/type-element-net-native.md) elementy obsługuje następujące typy zasad:  
  
-   `Activate`., Służy do sterowania dostępem środowiska uruchomieniowego konstruktorów, aby włączyć aktywacji wystąpień.  
  
-   `Browse`., Formanty wykonywania zapytania dotyczącego informacji o elementach programu, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.  
  
-   `Dynamic`., Sterowanie dostępem środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne.  
  
-   `Serialize`., Sterowanie dostępem środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić wystąpienia typu serializacji i serializowany przez bibliotek innych firm, takich jak serializator Newtonsoft JSON.  
  
-   `DataContractSerializer`., Określa zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.  
  
-   `DataContractJsonSerializer`., Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.  
  
-   `XmlSerializer`., Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.  
  
-   `MarshalObject`., Określa zasady dla przekazywanie typów referencyjnych do środowiska WinRT i modelu COM.  
  
-   `MarshalDelegate`., Określa zasady dla przekazywanie typów delegatów jako wskaźników funkcji do kodu natywnego.  
  
-   `MarshalStructure` . Określa zasady dla przekazywanie struktur do kodu natywnego.  
  
 Dostępne są następujące ustawienia skojarzone z tych typów zasad:  
  
-   `All`., Włącz zasady dla wszystkich typów i elementów członkowskich, które nie powoduje usunięcia łańcucha narzędzi.  
  
-   `Auto`., Zachowanie domyślne. (Nie określenie zasad jest równoznaczne z ustawieniem tej zasady `Auto` chyba, że ta zasada jest zastępowana, na przykład element nadrzędny.)  
  
-   `Excluded`., Wyłącz zasady dla elementu programu.  
  
-   `Public`., Włącz zasady dla typy publiczne lub elementy członkowskie, chyba że łańcucha narzędzi Określa, że element członkowski nie jest konieczne i w związku z tym spowoduje usunięcie jej. (W tym drugim przypadku należy użyć `Required Public` do upewnij się, że element członkowski jest przechowywana i funkcję odbicia.)  
  
-   `PublicAndInternal`., Włącz zasady dla publicznych i wewnętrznych typów albo elementów członkowskich, jeśli łańcucha narzędzi nie powoduje usunięcia ich.  
  
-   `Required Public`., Wymagają łańcucha narzędzi, aby zachować typy publiczne i elementów członkowskich, czy są używane, a następnie włączyć ją dla nich.  
  
-   `Required PublicAndInternal`., Wymagają łańcucha narzędzi, aby zachować zarówno typów publicznych oraz wewnętrznych, jak i elementów członkowskich, czy są używane, a następnie włączyć ją dla nich.  
  
-   `Required All`., Wymagają łańcucha narzędzi, aby zachować wszystkie typy i składniki, czy są używane, a następnie włączyć ją dla nich.  
  
 Na przykład następujący plik dyrektyw środowiska uruchomieniowego definiuje zasady dla wszystkich typów i członków w zestawie DataClasses.dll. Umożliwia ona odbicia dla serializacji wszystkie właściwości publiczne, umożliwia przeglądanie dla wszystkich typów i członków typu umożliwia aktywację dla wszystkich typów (z powodu `Dynamic` atrybut) i umożliwia odbicia wszystkie typy publiczne i elementów członkowskich.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"   
                Browse="All" Activate="PublicAndInternal"   
                Dynamic="Public"  />  
   </Application>  
   <Library Name="UtilityLibrary">  
     <!-- Child elements go here -->    
   </Library>  
</Directives>  
```  
  
### <a name="specifying-policy-for-members"></a>Określanie zasad dla elementów członkowskich  
 [Właściwości](../../../docs/framework/net-native/property-element-net-native.md) i [pola](../../../docs/framework/net-native/field-element-net-native.md) elementy obsługuje następujące typy zasad:  
  
-   `Browse`-Formanty wykonywania zapytania dotyczącego informacji na temat tego elementu członkowskiego, ale nie umożliwia dostęp do wszystkich środowiska wykonawczego.  
  
-   `Dynamic`-Kontroluje dostęp środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne. Kontroluje również wykonywania zapytania dotyczącego informacji na temat typu zawierającego.  
  
-   `Serialize`— Umożliwia sterowanie dostępem środowiska uruchomieniowego do elementu członkowskiego, aby włączyć wystąpienia typu serializacji i deserializacji przez biblioteki, takich jak serializator Newtonsoft JSON. Ta zasada będzie stosowana do konstruktorów, pól i właściwości.  
  
 [Metody](../../../docs/framework/net-native/method-element-net-native.md) i [zdarzeń](../../../docs/framework/net-native/event-element-net-native.md) elementy obsługuje następujące typy zasad:  
  
-   `Browse`-Formanty wykonywania zapytania dotyczącego informacji na temat tego elementu członkowskiego, ale nie włączyć dostęp do wszystkich środowiska wykonawczego.  
  
-   `Dynamic`-Kontroluje dostęp środowiska uruchomieniowego do wszystkie elementy członkowskie typu, łącznie z konstruktorów, metod, pola, właściwości i zdarzeń, aby umożliwić programowanie dynamiczne. Kontroluje również wykonywania zapytania dotyczącego informacji na temat typu zawierającego.  
  
 Dostępne są następujące ustawienia skojarzone z tych typów zasad:  
  
-   `Auto`-Zachowanie domyślne. (Nie określenie zasad jest równoznaczne z ustawieniem tej zasady `Auto` chyba, że coś zastępuje go.)  
  
-   `Excluded`-Nigdy nie zawierają metadanych dla elementu członkowskiego.  
  
-   `Included`-Włącz zasady, jeśli typ nadrzędny znajduje się w danych wyjściowych.  
  
-   `Required`-Wymagają łańcucha narzędzi, aby zachować ten element członkowski nawet wtedy, gdy jest używana i Włącz dla niej zasady.  
  
## <a name="runtime-directives-file-semantics"></a>Semantyka pliku dyrektyw środowiska uruchomieniowego  
 Zasady można definiować jednocześnie elementów wyższego poziomu oraz niższych poziomach. Na przykład zasady można definiować dla zestawu i dla niektórych typów zawartych w tym zestawie. Jeśli dany element niższego poziomu nie jest reprezentowany, dziedziczy zasady jego elementu nadrzędnego. Na przykład jeśli `Assembly` element jest obecny, ale `Type` elementy nie są określone zasady w `Assembly` element dotyczy poszczególnych typów w zestawie. Wiele elementów może także zastosować zasady do tego samego elementu programu. Przykładowo oddzielne [zestawu](../../../docs/framework/net-native/assembly-element-net-native.md) elementy zdefiniować tego samego elementu zasad dla tego samego zestawu inaczej. W poniższych sekcjach opisano, jak zasady dla danego typu zostanie rozwiązany w takich przypadkach.  
  
 A [typu](../../../docs/framework/net-native/type-element-net-native.md) lub [metody](../../../docs/framework/net-native/method-element-net-native.md) elementu typu ogólnego lub metody dotyczy wszystkich wystąpień, które nie mają własnych zasad polityki. Na przykład `Type` element, który określa zasady dla <xref:System.Collections.Generic.List%601> ma zastosowanie do skonstruowanego wszystkich wystąpień tego typu ogólnego, chyba że jest on przesłaniany dla określonego skonstruować typu ogólnego (takich jak `List<Int32>`) przez `TypeInstantiation` elementu. W przeciwnym razie elementy zasady zdefiniowane dla elementu program o nazwie.  
  
 Gdy element jest niejednoznaczny, aparat wyszukuje zgodny, a jeśli zostaną znalezione dopasowanie dokładne, użyje on. W przypadku odnalezienia wielu dopasowań, będzie ostrzeżenia lub błędu.  
  
### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Jeśli dwa dyrektywy zasady zastosowane do tego samego elementu programu  
 Jeśli dwa elementy w plikach dyrektywy środowiska uruchomieniowego różnych spróbuj ustawić różne wartości tego samego typu zasad dla tego samego elementu programu (na przykład zestawu lub typ), konflikt został rozwiązany w następujący sposób:  
  
1.  Jeśli `Excluded` element jest obecny, ma pierwszeństwo.  
  
2.  `Required`ma pierwszeństwo przez nie `Required`.  
  
3.  `All`ma pierwszeństwo przed `PublicAndInternal`, który ma pierwszeństwo przed `Public`.  
  
4.  Wszelkie jawne ustawienie ma pierwszeństwo przed `Auto`.  
  
 Na przykład, jeśli jeden projekt zawiera następujące dwa pliki dyrektyw środowiska uruchomieniowego, zasady serializacji dla DataClasses.dll ustawiono zarówno do `Required Public` i `All`. W takim przypadku zasady serializacji byłoby rozpoznana jako `Required All`.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"/>  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="All" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
 Jednak jeśli dwie dyrektywy w pliku dyrektyw środowiska uruchomieniowego pojedynczego spróbuj ustawić tego samego typu zasad dla tego samego elementu programu, narzędzie definicję schematu XML Wyświetla komunikat o błędzie.  
  
### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Jeśli elementy nadrzędnym a podrzędnym Zastosuj ten sam typ zasad  
 Elementy podrzędne zastąpienia ich elementów nadrzędnych, w tym `Excluded` ustawienie. Zastępowanie jest główną przyczyną, czy chcesz określić `Auto`.  
  
 W poniższym przykładzie ustawienie dla wszystkich elementów w zasad serializacji `DataClasses` który nie znajduje się w `DataClasses.ViewModels` będzie `Required Public`, a wszystko, co jest zarówno `DataClasses` i `DataClasses.ViewModels` będzie `All`.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
   </Appliction>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Jeśli ogólne otwarte i wystąpień elementów Zastosuj ten sam typ zasad  
 W poniższym przykładzie `Dictionary<int,int>` przypisano `Browse` zasady tylko wtedy, gdy aparat kolejny powód, aby nadać mu `Browse` zasad (który byłby domyślne zachowanie); co inne wystąpienia <xref:System.Collections.Generic.Dictionary%602> mają wszystkie jej elementów członkowskich umożliwia przeglądania.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
      <Namespace Name="DataClasses.Generics" />  
      <Type Name="Dictionary" Browse="All" />  
      <TypeInstantiation Name="Dictionary"   
                         Arguments="System.Int32,System.Int32" Browse="Auto" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="how-policy-is-inferred"></a>Jak jest wywnioskowany zasad  
 Każdy typ zasad ma inny zestaw reguł, które określają, jak obecności tego typu zasad wpływa inne konstrukcje.  
  
#### <a name="the-effect-of-browse-policy"></a>Wpływu zasad przeglądania  
 Stosowanie `Browse` zasady do typu obejmuje następujące zmiany zasad:  
  
-   Typ podstawowy typu jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli typ jest rodzajowy wystąpień, wersja bez wystąpień tego typu jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli typ jest delegatem, `Invoke` metody na typ jest oznaczony atrybutem `Dynamic` zasad.  
  
-   Każdy interfejs typu jest oznaczony atrybutem `Browse` zasad.  
  
-   Typ każdy atrybut zastosowany do typu jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli typ jest rodzajowy, każdy typ ograniczenia jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli typ jest rodzajowy, typów, na których jest utworzyć wystąpienia typu są oznaczone ikoną z `Browse` zasad.  
  
 Stosowanie `Browse` zasad do metody obejmuje następujące zmiany zasad:  
  
-   Każdy typ parametru metody jest oznaczony atrybutem `Browse` zasad.  
  
-   Zwracany typ metody jest oznaczony atrybutem `Browse` zasad.  
  
-   Typ zawierający metody jest oznaczony atrybutem `Browse` zasad.  
  
-   W przypadku metody skonkretyzowanej metody rodzajowej bez wystąpień ogólnego metoda jest oznaczona atrybutem `Browse` zasad.  
  
-   Typ każdy atrybut zastosowany do metody jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli metody jest rodzajowy, każdy typ ograniczenia jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli metody jest rodzajowy, typów, na których zostanie uruchomiony metody są oznaczone ikoną z `Browse` zasad.  
  
 Stosowanie `Browse` zasad do pola obejmuje następujące zmiany zasad:  
  
-   Typ każdego atrybutu zastosować do tego pola jest oznaczony atrybutem `Browse` zasad.  
  
-   Typ pola jest oznaczony atrybutem `Browse` zasad.  
  
-   Typ, do którego należy pole jest oznaczony atrybutem `Browse` zasad.  
  
#### <a name="the-effect-of-dynamic-policy"></a>Efekt zasady dynamicznego  
 Stosowanie `Dynamic` zasady do typu obejmuje następujące zmiany zasad:  
  
-   Typ podstawowy typu jest oznaczony atrybutem `Dynamic` zasad.  
  
-   Jeśli typ jest rodzajowy wystąpień, wersja bez wystąpień tego typu jest oznaczony atrybutem `Dynamic` zasad.  
  
-   Jeśli typ jest typem obiektu delegowanego `Invoke` metody na typ jest oznaczony atrybutem `Dynamic` zasad.  
  
-   Każdy interfejs typu jest oznaczony atrybutem `Browse` zasad.  
  
-   Typ każdy atrybut zastosowany do typu jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli typ jest rodzajowy, każdy typ ograniczenia jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli typ jest rodzajowy, typów, na których jest utworzyć wystąpienia typu są oznaczone ikoną z `Browse` zasad.  
  
 Stosowanie `Dynamic` zasad do metody obejmuje następujące zmiany zasad:  
  
-   Każdy typ parametru metody jest oznaczony atrybutem `Browse` zasad.  
  
-   Zwracany typ metody jest oznaczony atrybutem `Dynamic` zasad.  
  
-   Typ zawierający metody jest oznaczony atrybutem `Dynamic` zasad.  
  
-   W przypadku metody skonkretyzowanej metody rodzajowej bez wystąpień ogólnego metoda jest oznaczona atrybutem `Browse` zasad.  
  
-   Typ każdy atrybut zastosowany do metody jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli metody jest rodzajowy, każdy typ ograniczenia jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli metody jest rodzajowy, typów, na których zostanie uruchomiony metody są oznaczone ikoną z `Browse` zasad.  
  
-   Metoda może być wywoływany przez `MethodInfo.Invoke`, i utworzenia delegata staje się możliwe przez <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.  
  
 Stosowanie `Dynamic` zasad do pola obejmuje następujące zmiany zasad:  
  
-   Typ każdego atrybutu zastosować do tego pola jest oznaczony atrybutem `Browse` zasad.  
  
-   Typ pola jest oznaczony atrybutem `Dynamic` zasad.  
  
-   Typ, do którego należy pole jest oznaczony atrybutem `Dynamic` zasad.  
  
#### <a name="the-effect-of-activation-policy"></a>Wpływu zasad aktywacji  
 Zastosowanie zasad aktywacji z typem obejmuje następujące zmiany zasad:  
  
-   Jeśli typ jest rodzajowy wystąpień, wersja bez wystąpień tego typu jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli typ jest typem obiektu delegowanego `Invoke` metody na typ jest oznaczony atrybutem `Dynamic` zasad.  
  
-   Konstruktory typu są oznaczone ikoną z `Activation` zasad.  
  
 Stosowanie `Activation` zasad do metody obejmuje następujące zmiany zasad:  
  
-   Konstruktor może być wywoływany przez <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> i <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody. W przypadku metod `Activation` zasady wpływają tylko konstruktorów.  
  
 Stosowanie `Activation` zasada do pola nie ma znaczenia.  
  
#### <a name="the-effect-of-serialize-policy"></a>Wpływu zasad serializacja  
 `Serialize` Zasad umożliwia korzystanie z typowych serializatorów oparty na odbiciu. Jednak ponieważ wzorców dostępu dokładne odbicie serializatorów innych niż Microsoft nie są znane do firmy Microsoft, te zasady nie można całkowicie skuteczne.  
  
 Stosowanie `Serialize` zasady do typu obejmuje następujące zmiany zasad:  
  
-   Typ podstawowy typu jest oznaczony atrybutem `Serialize` zasad.  
  
-   Jeśli typ jest rodzajowy wystąpień, wersja bez wystąpień tego typu jest oznaczony atrybutem `Browse` zasad.  
  
-   Jeśli typ jest typem obiektu delegowanego `Invoke` metody na typ jest oznaczony atrybutem `Dynamic` zasad.  
  
-   Jeśli typ to wyliczenie tablicy tego typu jest oznaczony atrybutem `Serialize` zasad.  
  
-   Jeśli typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` jest oznaczony atrybutem `Serialize` zasad.  
  
-   Jeśli typ jest <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, lub <xref:System.Collections.Generic.IReadOnlyList%601>, następnie `T[]` i <xref:System.Collections.Generic.List%601> oznaczonych `Serialize` zasad., ale żaden z elementów typu interfejsu są oznaczone ikoną z `Serialize`zasad.  
  
-   Jeśli typ jest <xref:System.Collections.Generic.List%601>, żadnych elementów członkowskich tego typu są oznaczone ikoną z `Serialize` zasad.  
  
-   Jeśli typ jest <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> jest oznaczony atrybutem `Serialize` zasad. ale żadnych elementów członkowskich tego typu są oznaczone ikoną z `Serialize` zasad.  
  
-   Jeśli typ jest <xref:System.Collections.Generic.Dictionary%602>, żadnych elementów członkowskich tego typu są oznaczone ikoną z `Serialize` zasad.  
  
-   Jeśli typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` i `TValue` są oznaczone ikoną z `Serialize` zasad.  
  
-   Każdy konstruktora, każdej metody dostępu właściwości i każde pole jest oznaczony atrybutem `Serialize` zasad.  
  
 Stosowanie `Serialize` zasad do metody obejmuje następujące zmiany zasad:  
  
-   Typ zawierający jest oznaczony atrybutem `Serialize` zasad.  
  
-   Zwracany typ metody jest oznaczony atrybutem `Serialize` zasad.  
  
 Stosowanie `Serialize` zasad do pola obejmuje następujące zmiany zasad:  
  
-   Typ zawierający jest oznaczony atrybutem `Serialize` zasad.  
  
-   Typ pola jest oznaczony atrybutem `Serialize` zasad.  
  
#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserialier-policies"></a>Wpływ zasad XmlSerializer, DataContractSerializer i DataContractJsonSerialier  
 W odróżnieniu od `Serialize` zasad, które jest przeznaczony dla oparty na odbiciu serializatorów, `XmlSerializer`, `DataContractSerializer`, i `DataContractJsonSerializer` zasady są używane do włączenia zestaw serializatorów, które nie są [!INCLUDE[net_native](../../../includes/net-native-md.md)] narzędzia łańcucha. Nie zaimplementowano te serializatorów przy użyciu odbicia, ale zestaw typów, które można serializować w czasie wykonywania jest określana w podobny sposób jak typy, które są, które można odzwierciedlać.  
  
 Zastosowanie jednej z tych zasad na typ umożliwia typu, który ma być serializowany z pasujących serializatora. Ponadto żadnych typów, które mechanizm serializacji statycznie można określić jako wymagające serializacji również podlegać serializacji.  
  
 Te zasady nie mają wpływu na metody lub pola.  
  
 Aby uzyskać więcej informacji, zobacz sekcję "Różnice w serializatorów" w [migrowanie aplikacji ze Sklepu Windows Your do platformy .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)

---
title: Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c6f1a2d23d5f33ba7e4f0d51f795e75d7cf785e
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052451"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)

Dyrektywy środowiska uruchomieniowego (. rd.xml) plik znajduje się plik konfiguracyjny XML, który określa, czy elementy wyznaczonej programu są dostępne w celu odbicia. Poniżej przedstawiono przykładowy plik dyrektywy środowiska uruchomieniowego:

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

Dyrektywy środowiska uruchomieniowego plików używa `http://schemas.microsoft.com/netfx/2013/01/metadata` przestrzeni nazw.

Element główny jest [dyrektywy](../../../docs/framework/net-native/directives-element-net-native.md) elementu. Może zawierać zero lub więcej [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) elementy i zero lub jeden [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) elementu, jak pokazano na następującej strukturze. Atrybuty [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) elementu można zdefiniować całej aplikacji w czasie wykonywania odbicia zasad lub może służyć jako kontener dla elementów podrzędnych. [Biblioteki](../../../docs/framework/net-native/library-element-net-native.md) elementu, z drugiej strony, to po prostu kontener. Elementy podrzędne [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) i [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) zdefiniować elementy, typy, metody, pola, właściwości i zdarzenia, które są dostępne w celu odbicia.

Aby uzyskać informacje, wybierz elementy z następującej struktury, lub zobacz [elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md). W następującej hierarchii wielokropka oznacza struktury cyklicznej. Informacje w nawiasach wskazują, czy ten element jest opcjonalne lub wymagane, a jeśli jest używany, ile wystąpień (jednej lub wielu) są dozwolone.

[Dyrektywy](../../../docs/framework/net-native/directives-element-net-native.md) [1:1] [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) [0:1] [zestawu](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M]. . .
[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M] [podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1] [typu](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M]. . .
[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (typ zawierający jest atrybut) [O:1] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [parametru](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M] [ TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (skonstruowany metody ogólnej) [0:M] [właściwość](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [Pola](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [zdarzeń](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M] [typu](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M]. . .
[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [parametru](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M] [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) () skonstruowany metody ogólnej) [0:M] [właściwość](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [pola](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [zdarzeń](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) [0:M] [Zestawu](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M]. . .
[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M] [podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1] [typu](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M]. . .
[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (typ zawierający jest atrybut) [O:1] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (skonstruowany ogólny Metoda) [0:M] [właściwość](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [pola](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [zdarzeń](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0: M] [typu](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (skonstruowany typ rodzajowy) [0:M]. . .
[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (skonstruowany metody ogólnej) [0:M] [właściwość](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [pola](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [zdarzeń](../../../docs/framework/net-native/event-element-net-native.md)[0:M]

[Aplikacji](../../../docs/framework/net-native/application-element-net-native.md) element może mieć żadnych atrybutów lub może być atrybutów zasad omówione w [sekcji dyrektywy i zasad środowiska uruchomieniowego](#Directives).

A [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) element ma jeden atrybut `Name`, który określa nazwę biblioteki lub zestawu bez jego rozszerzenie pliku. Na przykład następująca [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) element ma zastosowanie do zestawu o nazwie Extensions.dll.

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

## <a name="runtime-directives-and-policy"></a>Dyrektywy środowiska uruchomieniowego i zasady

[Aplikacji](../../../docs/framework/net-native/application-element-net-native.md) samego elementu i elementy podrzędne [biblioteki](../../../docs/framework/net-native/library-element-net-native.md) i [aplikacji](../../../docs/framework/net-native/application-element-net-native.md) elementy express zasad; oznacza to, określają sposób, w którym można zastosować aplikacji odbicia do elementu programu. Typ zasad jest definiowany przez atrybut elementu (na przykład `Serialize`). Wartość zasad jest definiowany przez wartość atrybutu (na przykład `Serialize="Required"`).

Wszelkie zasady określone przez atrybut elementu ma zastosowanie do wszystkich elementów podrzędnych, które określać wartości dla tej zasady. Na przykład, jeśli zasady jest określona przez [typu](../../../docs/framework/net-native/type-element-net-native.md) elementy, które zasady mają zastosowanie do wszystkich zawartych typów i członków, dla których zasady nie jest jawnie określona.

Zasady, które mogą być wyrażone według [aplikacji](../../../docs/framework/net-native/application-element-net-native.md), [zestawu](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md), i [typu](../../../docs/framework/net-native/type-element-net-native.md) elementy różni się od zasad, które mogą być wyrażone dla poszczególnych elementów członkowskich (przez [metoda](../../../docs/framework/net-native/method-element-net-native.md), [właściwość](../../../docs/framework/net-native/property-element-net-native.md), [Pola](../../../docs/framework/net-native/field-element-net-native.md), i [zdarzeń](../../../docs/framework/net-native/event-element-net-native.md) elementów).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Określanie zasad dla zestawów, przestrzeni nazw i typów

[Aplikacji](../../../docs/framework/net-native/application-element-net-native.md), [zestawu](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md)i [ Typ](../../../docs/framework/net-native/type-element-net-native.md) elementy obsługuje następujących typów zasad:

- `Activate`. kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, aby włączyć aktywacji wystąpień.

- `Browse`. Kontroluje, wykonanie zapytania dotyczącego informacji o elementach programu, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.

- `Dynamic`. Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne.

- `Serialize`. Kontroluje dostęp do środowiska uruchomieniowego do konstruktorów, pola i właściwości, aby umożliwić wystąpienia typu, może być serializowany i przez bibliotek innych firm, takich jak serializator Newtonsoft JSON.

- `DataContractSerializer`. Określa zasady do serializacji, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.

- `DataContractJsonSerializer`. Określa zasady dla serializacji JSON, który używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.

- `XmlSerializer`. Określa zasady dla serializacji XML, który używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.

- `MarshalObject`. Określa zasady dla marshaling typów referencyjnych WinRT i modelu COM.

- `MarshalDelegate`. Określa zasady kierowanie typy delegatów jako wskaźniki funkcji do kodu macierzystego.

- `MarshalStructure` . Określa zasady marshalingu struktur do kodu macierzystego.

Dostępne są następujące ustawienia skojarzone z następujących typów zasad:

- `All`. Włącz zasady dla wszystkich typów i elementów członkowskich, które nie powoduje usunięcia łańcucha narzędzi.

- `Auto`. Użyj zachowania domyślnego. (Nie należy określać zasady jest równoznaczne z ustawieniem tej zasady `Auto` Jeśli te zasady nie zostanie zastąpiona, na przykład przez element nadrzędny.)

- `Excluded`. Wyłącz zasady dla elementu programu.

- `Public`. Włącz zasady, które dla publiczne typy lub członków, chyba że łańcucha narzędzi Określa, że składowa nie jest konieczne i w związku z tym powoduje jej usunięcie. (W tym drugim przypadku należy użyć `Required Public` do upewnij się, że składowa jest przechowywana możliwości odbicia.)

- `PublicAndInternal`. Włącz zasady dla publicznych i wewnętrznych typów ani elementów członkowskich, jeśli łańcuch narzędzi nie powoduje usunięcia ich.

- `Required Public`. Wymagają łańcucha narzędzi zapewnienie publicznego typów i członków, czy są one używane, a następnie włączyć ją dla nich.

- `Required PublicAndInternal`. Wymagają łańcucha narzędzi, aby zachować typów publicznych i wewnętrznych i członków, czy są one używane, a następnie włączyć ją dla nich.

- `Required All`. Wymagają łańcucha narzędzi, aby zachować wszystkie typy i elementy członkowskie, czy są one używane, a następnie włączyć ją dla nich.

Na przykład następujący plik dyrektywy środowiska uruchomieniowego definiuje zasady dla wszystkich typów i elementów członkowskich w zestawie DataClasses.dll. Umożliwia ona odbicia dla serializacji wszystkie właściwości publiczne umożliwia przeglądanie dla wszystkich typów i składowych typu umożliwia aktywację dla wszystkich typów (z powodu `Dynamic` atrybut) i umożliwia odbicia dla wszystkich typów publicznych i elementów członkowskich.

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

[Właściwość](../../../docs/framework/net-native/property-element-net-native.md) i [pola](../../../docs/framework/net-native/field-element-net-native.md) elementy obsługuje następujących typów zasad:

- `Browse` -Określa, wykonanie zapytania dotyczącego informacji na temat tego elementu członkowskiego, ale nie uwzględnia żadnych dostęp do środowiska uruchomieniowego.

- `Dynamic` -Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne. Kontroluje również wykonanie zapytania dotyczącego informacji na temat typu zawierającego.

- `Serialize` -Kontroluje dostęp do środowiska uruchomieniowego do elementu członkowskiego, aby umożliwić wystąpień typu serializacji i deserializacji, biblioteki, takie jak serializator Newtonsoft JSON. Te zasady mogą dotyczyć konstruktorów, pola i właściwości.

[Metoda](../../../docs/framework/net-native/method-element-net-native.md) i [zdarzeń](../../../docs/framework/net-native/event-element-net-native.md) elementy obsługuje następujących typów zasad:

- `Browse` — Kontroluje tworzenie zapytań dotyczących informacji na temat tego elementu członkowskiego, ale nie włączysz dostęp do dowolnego środowiska uruchomieniowego.

- `Dynamic` -Kontroluje dostęp do środowiska uruchomieniowego do wszystkich typów elementów członkowskich, konstruktorzy, metody, pola, właściwości i zdarzenia, w tym umożliwiające programowanie dynamiczne. Kontroluje również wykonanie zapytania dotyczącego informacji na temat typu zawierającego.

 Dostępne są następujące ustawienia skojarzone z następujących typów zasad:

- `Auto` -Używaj domyślnego zachowania. (Nie należy określać zasady jest równoznaczne z ustawieniem tej zasady `Auto` chyba, że coś, co zastępuje ją.)

- `Excluded` -Nigdy nie zawierają metadanych dla elementu członkowskiego.

- `Included` -Włącz zasady, jeśli typ nadrzędny znajduje się w danych wyjściowych.

- `Required` — Wymagają łańcucha narzędzi, aby zachować ten element członkowski nawet wtedy, gdy jest używana i włączona zasada.

## <a name="runtime-directives-file-semantics"></a>Semantykę plików dyrektywy środowiska uruchomieniowego

Zasady mogą być definiowane jednocześnie dla elementów wyższego poziomu i niższego poziomu. Na przykład zasad można zdefiniować dla zestawu, a także w niektórych typów zawartych w tym zestawie. Jeśli określony element niższego poziomu nie jest reprezentowane, dziedziczy zasady jego elementu nadrzędnego. Na przykład jeśli `Assembly` element jest obecny, ale `Type` elementy nie są określone zasady w `Assembly` element ma zastosowanie do poszczególnych typów w zestawie. Wiele elementów, można także zastosować zasady do tego samego elementu programu. Przykładowo oddzielne [zestawu](../../../docs/framework/net-native/assembly-element-net-native.md) elementów może zdefiniować tego samego elementu zasad dla tego samego zestawu inaczej. W poniższych sekcjach opisano, jak zasady dla danego typu zostanie rozwiązany w tych przypadkach.

A [typu](../../../docs/framework/net-native/type-element-net-native.md) lub [metoda](../../../docs/framework/net-native/method-element-net-native.md) elementu dla typu ogólnego lub metody stosuje swoje zasady do wszystkich wystąpień, które nie mają własnych zasad. Na przykład `Type` element, który określa zasady dla <xref:System.Collections.Generic.List%601> ma zastosowanie do wszystkich wystąpień skonstruowanego typu ogólnego, chyba że zostanie on przesłonięty dla określonego skonstruowany typ rodzajowy (takie jak `List<Int32>`) przez `TypeInstantiation` elementu. W przeciwnym razie elementy Zdefiniuj zasady dla elementu programu o nazwie.

Gdy element jest niejednoznaczny, aparat wyszukuje dopasowań, a jeśli zostaną znalezione dokładne dopasowanie, użyje on. W przypadku odnalezienia wielu dopasowań, nastąpi ostrzeżenia lub błędu.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Jeśli dwie dyrektywy zastosowanie zasad do tego samego elementu programu

Jeśli dwa elementy w plikach dyrektywy środowiskiem uruchomieniowym w różnych próbuje ustawić ten sam typ zasad dla tego samego elementu programu (na przykład zestawu lub typ) na różne wartości, ten konflikt został rozwiązany w następujący sposób:

1. Jeśli `Excluded` element jest obecny, ma pierwszeństwo.

2. `Required` pierwszeństwo ma ponad nie `Required`.

3. `All` ma pierwszeństwo przed `PublicAndInternal`, który ma pierwszeństwo przed `Public`.

4. Wszystkie jawne ustawienie ma pierwszeństwo przed `Auto`.

Na przykład, jeśli jeden projekt obejmuje następujące dwa pliki dyrektyw środowiska uruchomieniowego, zasada serializacji dla DataClasses.dll jest ustawiona na wartość oba `Required Public` i `All`. W tym przypadku zasada serializacji będą rozpoznawane jako `Required All`.

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

Jednak jeśli dwie dyrektywy w pliku dyrektyw środowiska uruchomieniowego pojedynczego próbuje ustawić ten sam typ zasad dla tego samego elementu programu, narzędzie definicji schematu XML Wyświetla komunikat o błędzie.

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Jeśli elementami nadrzędnymi i podrzędnymi zastosować ten sam typ zasad

Elementy podrzędne zastąpienia ich elementów nadrzędnych, w tym `Excluded` ustawienie. Zastępowanie jest głównym powodem, aby określić `Auto`.

W poniższym przykładzie ustawienie dla wszystkich elementów w zasad serializacji `DataClasses` który nie znajduje się w `DataClasses.ViewModels` będzie `Required Public`i wszystko, co znajduje się w obu `DataClasses` i `DataClasses.ViewModels` będzie `All`.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Jeśli otwarte typy ogólne i wystąpień elementów zastosować ten sam typ zasad

W poniższym przykładzie `Dictionary<int,int>` przypisano `Browse` zasady tylko wtedy, gdy aparat kolejny powód, aby nadać mu `Browse` zasad, (która mogłaby być domyślne zachowanie); co inne wystąpienia <xref:System.Collections.Generic.Dictionary%602> będzie miał wszystkie jej członków można przeglądać.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
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

### <a name="how-policy-is-inferred"></a>Jak wynika zasad

Każdy typ zasad ma inny zestaw reguł, które określają, jak obecności tego typu zasad wpływa inne konstrukcje.

#### <a name="the-effect-of-browse-policy"></a>Efekt zasad przeglądania

Stosowanie `Browse` zasad z typem obejmuje następujące zmiany zasad:

- Typ bazowy tego typu jest oznaczona za pomocą `Browse` zasad.

- Jeśli typ jest skonkretyzowany ogólny, bez wystąpień wersji typu, jest oznaczona za pomocą `Browse` zasad.

- Jeśli typ jest delegatem, `Invoke` metoda w typie jest oznaczona atrybutem `Dynamic` zasad.

- Każdy interfejs typu jest oznaczona za pomocą `Browse` zasad.

- Typ każdego atrybutu stosowane do typu jest oznaczona za pomocą `Browse` zasad.

- W przypadku typu ogólnego poszczególnych typów ograniczeń, jest oznaczona za pomocą `Browse` zasad.

- W przypadku typu ogólnego są oznaczone typów, na których zostanie uruchomiony, typ `Browse` zasad.

Stosowanie `Browse` zasady z metodą obejmuje następujące zmiany zasad:

- Każdy typ parametru metody oznaczonej przy użyciu `Browse` zasad.

- Zwracany typ metody oznaczonej przy użyciu `Browse` zasad.

- Typ zawierający metody oznaczonej przy użyciu `Browse` zasad.

- Jeśli metoda jest skonkretyzowany metody rodzajowej, metoda ogólny bez wystąpień jest oznaczony za pomocą `Browse` zasad.

- Typ każdego zastosowany do metody oznaczonej przy użyciu `Browse` zasad.

- Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczona za pomocą `Browse` zasad.

- Jeśli metoda jest ogólna, typów, na których zostanie uruchomiony, metoda są oznaczone `Browse` zasad.

Stosowanie `Browse` zasad do pola obejmuje następujące zmiany zasad:

- Typ atrybutu, każda zastosowana do pola jest oznaczona za pomocą `Browse` zasad.

- Typ pola jest oznaczona za pomocą `Browse` zasad.

- Typ, do której należy pole jest oznaczona za pomocą `Browse` zasad.

#### <a name="the-effect-of-dynamic-policy"></a>Efekt zasad dynamiczne

Stosowanie `Dynamic` zasad z typem obejmuje następujące zmiany zasad:

- Typ bazowy tego typu jest oznaczona za pomocą `Dynamic` zasad.

- Jeśli typ jest skonkretyzowany ogólny, bez wystąpień wersji typu, jest oznaczona za pomocą `Dynamic` zasad.

- Jeśli typ jest typem delegowanym `Invoke` metoda w typie jest oznaczona atrybutem `Dynamic` zasad.

- Każdy interfejs typu jest oznaczona za pomocą `Browse` zasad.

- Typ każdego atrybutu stosowane do typu jest oznaczona za pomocą `Browse` zasad.

- W przypadku typu ogólnego poszczególnych typów ograniczeń, jest oznaczona za pomocą `Browse` zasad.

- W przypadku typu ogólnego są oznaczone typów, na których zostanie uruchomiony, typ `Browse` zasad.

Stosowanie `Dynamic` zasady z metodą obejmuje następujące zmiany zasad:

- Każdy typ parametru metody oznaczonej przy użyciu `Browse` zasad.

- Zwracany typ metody oznaczonej przy użyciu `Dynamic` zasad.

- Typ zawierający metody oznaczonej przy użyciu `Dynamic` zasad.

- Jeśli metoda jest skonkretyzowany metody rodzajowej, metoda ogólny bez wystąpień jest oznaczony za pomocą `Browse` zasad.

- Typ każdego zastosowany do metody oznaczonej przy użyciu `Browse` zasad.

- Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczona za pomocą `Browse` zasad.

- Jeśli metoda jest ogólna, typów, na których zostanie uruchomiony, metoda są oznaczone `Browse` zasad.

- Metoda może być wywoływany przez `MethodInfo.Invoke`, i tworzenia delegata staje się możliwe poprzez <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.

Stosowanie `Dynamic` zasad do pola obejmuje następujące zmiany zasad:

- Typ atrybutu, każda zastosowana do pola jest oznaczona za pomocą `Browse` zasad.

- Typ pola jest oznaczona za pomocą `Dynamic` zasad.

- Typ, do której należy pole jest oznaczona za pomocą `Dynamic` zasad.

#### <a name="the-effect-of-activation-policy"></a>Efekt zasad aktywacji

Zastosowanie zasad aktywacji z typem obejmuje następujące zmiany zasad:

- Jeśli typ jest skonkretyzowany ogólny, bez wystąpień wersji typu, jest oznaczona za pomocą `Browse` zasad.

- Jeśli typ jest typem delegowanym `Invoke` metoda w typie jest oznaczona atrybutem `Dynamic` zasad.

- Konstruktory tego typu są oznaczone `Activation` zasad.

Stosowanie `Activation` zasady z metodą obejmuje następujące zmiany zasad:

- Konstruktor może być wywoływany przez <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> i <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody. W przypadku metod `Activation` zasady wpływają tylko konstruktory.

Stosowanie `Activation` zasada do pola nie ma znaczenia.

#### <a name="the-effect-of-serialize-policy"></a>Efekt zasad serializacja

`Serialize` Zasad umożliwia korzystanie z typowych serializatory oparty na odbiciu. Jednak ponieważ wzorców dostępu dokładne odbicie serializatory firm innych niż Microsoft nie są znane do firmy Microsoft, ta zasada może nie być całkowicie skuteczne.

Stosowanie `Serialize` zasad z typem obejmuje następujące zmiany zasad:

- Typ bazowy tego typu jest oznaczona za pomocą `Serialize` zasad.

- Jeśli typ jest skonkretyzowany ogólny, bez wystąpień wersji typu, jest oznaczona za pomocą `Browse` zasad.

- Jeśli typ jest typem delegowanym `Invoke` metoda w typie jest oznaczona atrybutem `Dynamic` zasad.

- Jeśli typ jest wyliczeniem, tablicy tego typu jest oznaczona za pomocą `Serialize` zasad.

- Jeśli typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` jest oznaczona za pomocą `Serialize` zasad.

- Jeśli typ jest <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, lub <xref:System.Collections.Generic.IReadOnlyList%601>, następnie `T[]` i <xref:System.Collections.Generic.List%601> oznaczone `Serialize` zasadami, ale nie elementy członkowskie typu interfejsu są oznaczone `Serialize`zasad.

- Jeśli typ jest <xref:System.Collections.Generic.List%601>, nie elementy członkowskie tego typu są oznaczone `Serialize` zasad.

- Jeśli typ jest <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> jest oznaczona za pomocą `Serialize` zasad. ale nie elementy członkowskie tego typu są oznaczone `Serialize` zasad.

- Jeśli typ jest <xref:System.Collections.Generic.Dictionary%602>, nie elementy członkowskie tego typu są oznaczone `Serialize` zasad.

- Jeśli typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` i `TValue` są oznaczone `Serialize` zasad.

- Każdy Konstruktor, każda metoda dostępu do właściwości i każde pole jest oznaczona za pomocą `Serialize` zasad.

Stosowanie `Serialize` zasady z metodą obejmuje następujące zmiany zasad:

- Typ zawierający jest oznaczona za pomocą `Serialize` zasad.

- Zwracany typ metody oznaczonej przy użyciu `Serialize` zasad.

Stosowanie `Serialize` zasad do pola obejmuje następujące zmiany zasad:

- Typ zawierający jest oznaczona za pomocą `Serialize` zasad.

- Typ pola jest oznaczona za pomocą `Serialize` zasad.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>Efekt zasad XmlSerializer, DataContractSerializer i klasa DataContractJsonSerializer

W odróżnieniu od `Serialize` zasad, które mają być oparty na odbiciu serializatory, <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> zasady są używane do włączenia zbiór serializatory, które są znane z łańcucha narzędzi .NET Native. Serializatory te nie są implementowane przy użyciu odbicia, ale zestaw typów, które może być serializowany w czasie wykonywania, jest określana w podobny sposób jak typy, które są reflectable.

Zastosowanie jednej z tych zasad do typu umożliwia typu, który ma być serializowany z pasujących serializatora. Ponadto wszystkie typy, które mechanizm serializacji statycznie można określić jako wymagające serializacji również podlegać serializacji.

Te zasady nie mają wpływu na metody lub pola.

Aby uzyskać więcej informacji, zobacz sekcję "Różnice w Serializatory" w [Migrowanie Your Windows Store aplikacji platformy .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).

## <a name="see-also"></a>Zobacz także

- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)

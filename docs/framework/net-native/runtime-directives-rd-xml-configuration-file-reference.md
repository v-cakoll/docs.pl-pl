---
title: Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adfc0ae6d9bdae333daacee525c7775acd5a8029
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049139"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)

Plik dyrektywy środowiska uruchomieniowego (. Rd. xml) jest plikiem konfiguracji XML, który określa, czy wyszukane elementy programu są dostępne do odbicia. Oto przykład pliku dyrektywy środowiska uruchomieniowego:

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

## <a name="the-structure-of-a-runtime-directives-file"></a>Struktura pliku dyrektywy środowiska uruchomieniowego

Plik dyrektywy środowiska uruchomieniowego używa `http://schemas.microsoft.com/netfx/2013/01/metadata` przestrzeni nazw.

Elementem głównym jest element [dyrektywy](directives-element-net-native.md) . Może zawierać zero lub więcej elementów [biblioteki](library-element-net-native.md) oraz zero lub jeden element [aplikacji](application-element-net-native.md) , jak pokazano w poniższej strukturze. Atrybuty elementu [aplikacji](application-element-net-native.md) mogą definiować zasady odbicia w środowisku uruchomieniowym dla całej aplikacji lub mogą one stanowić kontener dla elementów podrzędnych. Element [biblioteki](library-element-net-native.md) , z drugiej strony, jest po prostu kontenerem. Elementy podrzędne [aplikacji](application-element-net-native.md) i [biblioteki](library-element-net-native.md) definiują typy, metody, pola, właściwości i zdarzenia, które są dostępne do odbicia.

Aby uzyskać informacje referencyjne, wybierz elementy z następującej struktury lub zobacz [elementy dyrektywy środowiska uruchomieniowego](runtime-directive-elements.md). W poniższej hierarchii wielokropek oznacza strukturę cykliczną. Informacje w nawiasach wskazują, czy ten element jest opcjonalny, czy wymagany, a jeśli jest używany, ile wystąpień (jeden lub wiele) jest dozwolonych.

[Dyrektywy](directives-element-net-native.md) [1:1] [aplikacja](application-element-net-native.md) [0:1] [zestaw](assembly-element-net-native.md) [0: m] [przestrzeń nazw](namespace-element-net-native.md) [0: m]. . .
[Typ](type-element-net-native.md) [0: M]. . .
[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
[Przestrzeń nazw](namespace-element-net-native.md) [0: M] [Przestrzeń nazw](namespace-element-net-native.md) [0: M]. . .
[Typ](type-element-net-native.md) [0: M]. . .
[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
[Typ](type-element-net-native.md) [0: M] [Podtypy](subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1] [Typ](type-element-net-native.md) [0: M]. . .
[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
[AttributeImplies](attributeimplies-element-net-native.md) (zawierający typ jest atrybutem) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0: M] [Metoda](method-element-net-native.md) [0: M] [Parametr](parameter-element-net-native.md) [0: M] [TypeParameter](typeparameter-element-net-native.md) [0: M] [GenericParameter](genericparameter-element-net-native.md) [0: M] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M] [Właściwość](property-element-net-native.md) [0: M] [Pole](field-element-net-native.md) [0: M] [Zdarzenie](event-element-net-native.md) [0: M] [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M] [Typ](type-element-net-native.md) [0: M]. . .
[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
[Metoda](method-element-net-native.md) [0: M] [Parametr](parameter-element-net-native.md) [0: M] [TypeParameter](typeparameter-element-net-native.md) [0: M] [GenericParameter](genericparameter-element-net-native.md) [0: M] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M] [Właściwość](property-element-net-native.md) [0: M] [Pole](field-element-net-native.md) [0: M] [Zdarzenie](event-element-net-native.md) [0: M] [Biblioteka](library-element-net-native.md) [0: M] [Zestaw](assembly-element-net-native.md) [0: M] [Przestrzeń nazw](namespace-element-net-native.md) [0: M]. . .
[Typ](type-element-net-native.md) [0: M]. . .
[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
[Przestrzeń nazw](namespace-element-net-native.md) [0: M] [Przestrzeń nazw](namespace-element-net-native.md) [0: M]. . .
[Typ](type-element-net-native.md) [0: M]. . .
[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
[Typ](type-element-net-native.md) [0: M] [Podtypy](subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1] [Typ](type-element-net-native.md) [0: M]. . .
[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
[AttributeImplies](attributeimplies-element-net-native.md) (zawierający typ jest atrybutem) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0: M] [Metoda](method-element-net-native.md) [0: M] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M] [Właściwość](property-element-net-native.md) [0: M] [Pole](field-element-net-native.md) [0: M] [Zdarzenie](event-element-net-native.md) [0: M] [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M] [Typ](type-element-net-native.md) [0: M]. . .
[TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
[Metoda](method-element-net-native.md) [0: M] [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M] [Właściwość](property-element-net-native.md) [0: M] [Pole](field-element-net-native.md) [0: M] [Zdarzenie](event-element-net-native.md) [0: M]

Element [aplikacji](application-element-net-native.md) nie może mieć żadnych atrybutów lub atrybuty zasad mogą być omówione w [sekcji dyrektywy i zasad środowiska uruchomieniowego](#Directives).

Element [biblioteki](library-element-net-native.md) ma jeden atrybut, `Name`, który określa nazwę biblioteki lub zestawu, bez rozszerzenia pliku. Na przykład poniższy element [biblioteki](library-element-net-native.md) ma zastosowanie do zestawu o nazwie Extensions. dll.

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

## <a name="runtime-directives-and-policy"></a>Dyrektywy i zasady środowiska uruchomieniowego

Sam element [aplikacji](application-element-net-native.md) i elementy podrzędne [biblioteki](library-element-net-native.md) i elementów [aplikacji](application-element-net-native.md) Express Policy; oznacza to, że definiują sposób, w jaki aplikacja może zastosować odbicie do elementu programu. Typ zasad jest definiowany przez atrybut elementu (na przykład `Serialize`). Wartość zasad jest definiowana przez wartość atrybutu (na przykład `Serialize="Required"`).

Wszelkie zasady określone przez atrybut elementu mają zastosowanie do wszystkich elementów podrzędnych, które nie określają wartości dla tych zasad. Na przykład jeśli zasady są określone przez element [typu](type-element-net-native.md) , te zasady mają zastosowanie do wszystkich typów i elementów członkowskich, dla których zasady nie są jawnie określone.

Zasady, które mogą być wyrażone przez [aplikację](application-element-net-native.md), [zestaw](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [przestrzeń nazw](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)i elementy [typu](type-element-net-native.md) , różnią się od zasad, które mogą być wyrażone dla poszczególnych członków (przez [Metoda](method-element-net-native.md), [Właściwość](property-element-net-native.md), [pole](field-element-net-native.md)i elementy [zdarzenia](event-element-net-native.md) ).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Określanie zasad dla zestawów, przestrzeni nazw i typów

Elementy [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [podtyp](subtypes-element-net-native.md)i [Type](type-element-net-native.md) obsługują następujące typy zasad:

- `Activate`. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.

- `Browse`. Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.

- `Dynamic`. Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.

- `Serialize`. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i Serializowanie wystąpień typu przez biblioteki innych firm, takie jak serializator JSON Newtonsoft.

- `DataContractSerializer`. Kontroluje zasady dla serializacji, która używa <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.

- `DataContractJsonSerializer`. Kontroluje zasady dla serializacji JSON używającej <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> klasy.

- `XmlSerializer`. Kontroluje zasady dla serializacji XML, która używa <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> klasy.

- `MarshalObject`. Kontroluje zasady dotyczące organizowania typów odwołań do WinRT i COM.

- `MarshalDelegate`. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.

- `MarshalStructure` . Steruje zasadami organizowania struktur w kodzie natywnym.

Ustawienia skojarzone z tymi typami zasad są następujące:

- `All`. Włącz zasady dla wszystkich typów i elementów członkowskich, które nie są usuwane przez łańcuch narzędzi.

- `Auto`. Użyj zachowania domyślnego. (Nieokreślanie zasad jest równoznaczne z ustawieniem tych zasad `Auto` , chyba że te zasady zostaną zastąpione, na przykład przez element nadrzędny).

- `Excluded`. Wyłącz zasady dla elementu program.

- `Public`. Włącz zasady dla typów publicznych lub członków, chyba że łańcuch narzędzi nie ustali, że element członkowski jest niepotrzebny i usuwa go. (W tym drugim przypadku należy użyć `Required Public` , aby upewnić się, że element członkowski jest przechowywany i ma możliwości odbicia).

- `PublicAndInternal`. Włącz zasady dla typów publicznych i wewnętrznych lub członków, jeśli łańcuch narzędzi nie zostanie usunięty.

- `Required Public`. Należy wymagać łańcucha narzędzi, aby zachować publiczne typy i członków, niezależnie od tego, czy są one używane, i włączyć dla nich zasady.

- `Required PublicAndInternal`. Wymagaj, aby łańcuch narzędzi zachował typy publiczne i wewnętrzne oraz członków, niezależnie od tego, czy są one używane, i Włącz dla nich zasady.

- `Required All`. Wymagaj łańcucha narzędzi, aby zachować wszystkie typy i członków, niezależnie od tego, czy są one używane, i Włącz dla nich zasady.

Na przykład następujące pliki dyrektywy środowiska uruchomieniowego definiują zasady dla wszystkich typów i elementów członkowskich w zestawie DataClasses. dll. Umożliwia odbicie dla serializacji wszystkich właściwości publicznych, umożliwia przeglądanie dla wszystkich typów i elementów członkowskich typu, umożliwia aktywację dla wszystkich typów (z `Dynamic` powodu atrybutu) i umożliwia odbicie dla wszystkich typów publicznych i członków.

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

### <a name="specifying-policy-for-members"></a>Określanie zasad dla członków

Elementy [Właściwości](property-element-net-native.md) i [pól](field-element-net-native.md) obsługują następujące typy zasad:

- `Browse`-Kontroluje zapytania w celu uzyskania informacji dotyczących tego elementu członkowskiego, ale nie umożliwia dostępu do środowiska uruchomieniowego.

- `Dynamic`-Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne. Steruje także wykonywaniem zapytań dotyczących informacji o typie zawierającym.

- `Serialize`-Kontroluje dostęp środowiska uruchomieniowego do elementu członkowskiego, aby umożliwić serializacji i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON Newtonsoft. Te zasady można stosować do konstruktorów, pól i właściwości.

Elementy [Method](method-element-net-native.md) i [Event](event-element-net-native.md) obsługują następujące typy zasad:

- `Browse`-Kontroluje zapytania o informacje dotyczące tego elementu członkowskiego, ale nie włącza żadnego dostępu do środowiska uruchomieniowego.

- `Dynamic`-Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne. Steruje także wykonywaniem zapytań dotyczących informacji o typie zawierającym.

 Ustawienia skojarzone z tymi typami zasad są następujące:

- `Auto`— Użyj zachowania domyślnego. (Nieokreślanie zasad jest równoznaczne z ustawieniem tych zasad `Auto` , chyba że coś zastępuje je).

- `Excluded`-Nigdy nie dołączaj metadanych dla elementu członkowskiego.

- `Included`-Włącz zasady, jeśli typ nadrzędny jest obecny w danych wyjściowych.

- `Required`-Wymagaj łańcucha narzędzi, aby zachować ten element członkowski nawet wtedy, gdy jest nieużywany, i Włącz dla niego zasady.

## <a name="runtime-directives-file-semantics"></a>Semantyka plików dyrektyw środowiska uruchomieniowego

Zasady można definiować jednocześnie dla elementów wyższego poziomu i niższego poziomu. Na przykład można zdefiniować zasady dla zestawu i dla niektórych typów zawartych w tym zestawie. Jeśli określony element niższego poziomu nie jest reprezentowany, dziedziczy on zasady jego elementu nadrzędnego. Na przykład jeśli `Assembly` element jest obecny, ale `Type` elementy nie są, zasady określone w `Assembly` elemencie mają zastosowanie do każdego typu w zestawie. Wiele elementów może również stosować zasady do tego samego elementu programu. Na przykład oddzielne elementy [zestawu](assembly-element-net-native.md) mogą definiować ten sam element zasad dla tego samego zestawu inaczej. W poniższych sekcjach wyjaśniono, w jaki sposób zasady dla określonego typu są rozwiązywane w tych przypadkach.

[Typ](type-element-net-native.md) lub element [metody](method-element-net-native.md) typu ogólnego lub metody stosuje zasady do wszystkich wystąpień, które nie mają własnych zasad. Na przykład `Type` element określający <xref:System.Collections.Generic.List%601> zasady dotyczą wszystkich skonstruowanych wystąpień tego typu ogólnego, chyba że zostanie przesłonięty dla określonego konstruowanego `List<Int32>`typu ogólnego (takiego `TypeInstantiation` jak) przez element. W przeciwnym razie elementy definiują zasady dla elementu programu o nazwie.

Gdy element jest niejednoznaczny, aparat szuka pasujących elementów i jeśli znajdzie dokładne dopasowanie, użyje go. Jeśli znajdzie wiele dopasowań, pojawi się ostrzeżenie lub błąd.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Jeśli dwie dyrektywy stosują zasady do tego samego elementu programu

Jeśli dwa elementy w różnych dyrektywach środowiska uruchomieniowego próbują ustawić ten sam typ zasad dla tego samego elementu programu (na przykład zestawu lub typu) do różnych wartości, konflikt zostanie rozwiązany w następujący sposób:

1. `Excluded` Jeśli element jest obecny, ma pierwszeństwo.

2. `Required`ma pierwszeństwo przed `Required`.

3. `All`ma pierwszeństwo `PublicAndInternal`przed, który ma `Public`pierwszeństwo przed.

4. Każde ustawienie jawne ma pierwszeństwo `Auto`przed.

Na przykład jeśli pojedynczy projekt zawiera następujące dwa pliki dyrektywy środowiska uruchomieniowego, zasady serializacji dla DataClasses. dll są ustawione na `Required Public` i. `All` W takim przypadku zasady serializacji byłyby rozpoznawane jako `Required All`.

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

Jeśli jednak dwie dyrektywy w jednym pliku dyrektywy środowiska uruchomieniowego próbują ustawić ten sam typ zasad dla tego samego programu, narzędzie definicji schematu XML wyświetli komunikat o błędzie.

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Jeśli elementy podrzędne i nadrzędne stosują ten sam typ zasad

Elementy podrzędne przesłaniają elementy nadrzędne, w `Excluded` tym ustawienie. Zastępowanie jest głównym powodem, który ma zostać `Auto`określony.

W poniższym przykładzie ustawienie zasad `DataClasses` serializacji dla wszystkiego w tym elemencie `DataClasses.ViewModels` nie `Required Public`jest, a `All`wszystko to w obu `DataClasses` i `DataClasses.ViewModels` .

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Jeśli otwarte elementy generyczne i wystąpienia mają zastosowanie tego samego typu zasad

W `Dictionary<int,int>` poniższym przykładzie `Browse` zasady są przypisywane tylko wtedy, gdy silnik ma kolejną przyczynę, `Browse` aby nadać mu zasady (które w przeciwnym razie byłyby <xref:System.Collections.Generic.Dictionary%602> zachowaniem domyślnym); każde inne wystąpienie będzie miało wszystkie jego członkowie umożliwia przeglądania.

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

### <a name="how-policy-is-inferred"></a>Jak zasady są wywnioskowane

Każdy typ zasad ma inny zestaw reguł, które określają, jak obecność tego typu zasad ma wpływ na inne konstrukcje.

#### <a name="the-effect-of-browse-policy"></a>Efekt przeglądania zasad

`Browse` Zastosowanie zasad do typu obejmuje następujące zmiany zasad:

- Typ podstawowy typu jest oznaczony przy użyciu `Browse` zasad.

- Jeśli typ jest ogólnym wystąpieniem, niewystępująca wersja typu jest oznaczona przy użyciu `Browse` zasad.

- Jeśli typ jest delegatem, `Invoke` Metoda typu jest oznaczona `Dynamic` przy użyciu zasad.

- Każdy interfejs typu jest oznaczony przy użyciu `Browse` zasad.

- Typ każdego atrybutu zastosowanego do typu jest oznaczony przy użyciu `Browse` zasad.

- Jeśli typ jest ogólny, każdy typ ograniczenia jest oznaczony przy użyciu `Browse` zasad.

- Jeśli typ jest ogólny, typy, w których tworzone jest wystąpienie typu są oznaczone `Browse` zasadami.

`Browse` Zastosowanie zasad do metody obejmuje następujące zmiany zasad:

- Każdy typ parametru metody jest oznaczony przy użyciu `Browse` zasad.

- Zwracany typ metody jest oznaczony przy użyciu `Browse` zasad.

- Typ zawierający metodę jest oznaczony przy użyciu `Browse` zasad.

- Jeśli metoda jest wystąpieniem metody generycznej, Metoda niebędąca wystąpieniem jest oznaczona przy użyciu `Browse` zasad.

- Typ każdego atrybutu zastosowanego do metody jest oznaczony przy użyciu `Browse` zasad.

- Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczony przy użyciu `Browse` zasad.

- Jeśli metoda jest ogólna, typy, w których tworzone jest wystąpienie metody są oznaczone `Browse` zasadami.

`Browse` Zastosowanie zasad do pola obejmuje następujące zmiany zasad:

- Typ każdego atrybutu zastosowanego do pola jest oznaczony przy użyciu `Browse` zasad.

- Typ pola jest oznaczony przy użyciu `Browse` zasad.

- Typ, do którego należy pole, jest oznaczony przy użyciu `Browse` zasad.

#### <a name="the-effect-of-dynamic-policy"></a>Efekt zasad dynamicznych

`Dynamic` Zastosowanie zasad do typu obejmuje następujące zmiany zasad:

- Typ podstawowy typu jest oznaczony przy użyciu `Dynamic` zasad.

- Jeśli typ jest ogólnym wystąpieniem, niewystępująca wersja typu jest oznaczona przy użyciu `Dynamic` zasad.

- Jeśli typ jest typem delegata, `Invoke` Metoda typu jest oznaczona `Dynamic` przy użyciu zasad.

- Każdy interfejs typu jest oznaczony przy użyciu `Browse` zasad.

- Typ każdego atrybutu zastosowanego do typu jest oznaczony przy użyciu `Browse` zasad.

- Jeśli typ jest ogólny, każdy typ ograniczenia jest oznaczony przy użyciu `Browse` zasad.

- Jeśli typ jest ogólny, typy, w których tworzone jest wystąpienie typu są oznaczone `Browse` zasadami.

`Dynamic` Zastosowanie zasad do metody obejmuje następujące zmiany zasad:

- Każdy typ parametru metody jest oznaczony przy użyciu `Browse` zasad.

- Zwracany typ metody jest oznaczony przy użyciu `Dynamic` zasad.

- Typ zawierający metodę jest oznaczony przy użyciu `Dynamic` zasad.

- Jeśli metoda jest wystąpieniem metody generycznej, Metoda niebędąca wystąpieniem jest oznaczona przy użyciu `Browse` zasad.

- Typ każdego atrybutu zastosowanego do metody jest oznaczony przy użyciu `Browse` zasad.

- Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczony przy użyciu `Browse` zasad.

- Jeśli metoda jest ogólna, typy, w których tworzone jest wystąpienie metody są oznaczone `Browse` zasadami.

- Metoda może być wywoływana przez `MethodInfo.Invoke`, a tworzenie delegatów jest możliwe przez. <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>

`Dynamic` Zastosowanie zasad do pola obejmuje następujące zmiany zasad:

- Typ każdego atrybutu zastosowanego do pola jest oznaczony przy użyciu `Browse` zasad.

- Typ pola jest oznaczony przy użyciu `Dynamic` zasad.

- Typ, do którego należy pole, jest oznaczony przy użyciu `Dynamic` zasad.

#### <a name="the-effect-of-activation-policy"></a>Efekt zasad aktywacji

Zastosowanie zasad aktywacji do typu wiąże się z następującymi zmianami zasad:

- Jeśli typ jest ogólnym wystąpieniem, niewystępująca wersja typu jest oznaczona przy użyciu `Browse` zasad.

- Jeśli typ jest typem delegata, `Invoke` Metoda typu jest oznaczona `Dynamic` przy użyciu zasad.

- Konstruktory typu są oznaczone `Activation` zasadami.

`Activation` Zastosowanie zasad do metody obejmuje następujące zmiany zasad:

- Konstruktor może być wywoływany przez <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> metody i. <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> W przypadku metod `Activation` zasady mają wpływ tylko na konstruktory.

`Activation` Zastosowanie zasad do pola nie ma żadnego skutku.

#### <a name="the-effect-of-serialize-policy"></a>Efekt serializacji zasad

`Serialize` Zasady umożliwiają korzystanie z typowych serializatorów opartych na odbiciach. Jednak ze względu na to, że wzorce dostępu do odbicia dla serializatorów firm innych niż Microsoft nie są znane firmie Microsoft, te zasady mogą nie być całkowicie skuteczne.

`Serialize` Zastosowanie zasad do typu obejmuje następujące zmiany zasad:

- Typ podstawowy typu jest oznaczony przy użyciu `Serialize` zasad.

- Jeśli typ jest ogólnym wystąpieniem, niewystępująca wersja typu jest oznaczona przy użyciu `Browse` zasad.

- Jeśli typ jest typem delegata, `Invoke` Metoda typu jest oznaczona `Dynamic` przy użyciu zasad.

- Jeśli typ jest wyliczeniem, tablica typu jest oznaczona przy użyciu `Serialize` zasad.

- Jeśli typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` jest oznaczony przy użyciu `Serialize` zasad.

- Jeśli typ ma <xref:System.Collections.Generic.IEnumerable%601>wartość, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601> ,,<xref:System.Collections.Generic.IReadOnlyList%601>lub ,`T[]` i<xref:System.Collections.Generic.List%601> jest oznaczony`Serialize` przy użyciu zasad., ale żaden element członkowski typu interfejsu nie jest oznaczony za pomocą <xref:System.Collections.Generic.IReadOnlyCollection%601> `Serialize`zasady.

- Jeśli typ ma wartość <xref:System.Collections.Generic.List%601>, żadne elementy członkowskie tego typu nie są oznaczone `Serialize` zasadami.

- Jeśli typ ma <xref:System.Collections.Generic.IDictionary%602>wartość, <xref:System.Collections.Generic.Dictionary%602> jest oznaczony przy użyciu `Serialize` zasad. ale żadne elementy członkowskie tego typu nie są oznaczone `Serialize` zasadami.

- Jeśli typ ma wartość <xref:System.Collections.Generic.Dictionary%602>, żadne elementy członkowskie tego typu nie są oznaczone `Serialize` zasadami.

- Jeśli <xref:System.Collections.Generic.IDictionary%602>typ implementuje `TKey` i`TValue`jest oznaczony przy użyciu zasad.`Serialize`

- Każdy Konstruktor, każdy akcesor właściwości i każde pole jest oznaczone `Serialize` zasadami.

`Serialize` Zastosowanie zasad do metody obejmuje następujące zmiany zasad:

- Typ zawierający jest oznaczony przy użyciu `Serialize` zasad.

- Zwracany typ metody jest oznaczony przy użyciu `Serialize` zasad.

`Serialize` Zastosowanie zasad do pola obejmuje następujące zmiany zasad:

- Typ zawierający jest oznaczony przy użyciu `Serialize` zasad.

- Typ pola jest oznaczony przy użyciu `Serialize` zasad.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>Wpływ zasad XmlSerializer, DataContractSerializer i Klasa DataContractJsonSerializer

W przeciwieństwie `Serialize` do zasad, które są przeznaczone dla serializatorów opartych na odbiciach <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer>, zasady <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , i są używane do włączania zestawu serializatorów, które są znane do łańcucha narzędzi .NET Native. Te serializacji nie są implementowane przy użyciu odbicia, ale zestaw typów, które mogą być serializowane w czasie wykonywania, jest określany w podobny sposób, jak typy, które są odzwierciedlane.

Zastosowanie jednej z tych zasad do typu umożliwia serializacji typu przy użyciu pasującego serializatora. Ponadto wszelkie typy, które aparat serializacji może statycznie określić, ponieważ wymaganie serializacji również będzie możliwe do serializacji.

Te zasady nie mają wpływu na metody lub pola.

Aby uzyskać więcej informacji, zobacz sekcję "różnice w Serializatorach" w temacie [Migrowanie aplikacji ze sklepu Windows do .NET Native](migrating-your-windows-store-app-to-net-native.md).

## <a name="see-also"></a>Zobacz także

- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Odbicie i architektura .NET Native](reflection-and-net-native.md)

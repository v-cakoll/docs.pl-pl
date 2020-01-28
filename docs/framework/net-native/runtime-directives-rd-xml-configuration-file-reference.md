---
title: Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738408"
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

Plik dyrektywy środowiska uruchomieniowego używa przestrzeni nazw `http://schemas.microsoft.com/netfx/2013/01/metadata`.

Elementem głównym jest element [dyrektywy](directives-element-net-native.md) . Może zawierać zero lub więcej elementów [biblioteki](library-element-net-native.md) oraz zero lub jeden element [aplikacji](application-element-net-native.md) , jak pokazano w poniższej strukturze. Atrybuty elementu [aplikacji](application-element-net-native.md) mogą definiować zasady odbicia w środowisku uruchomieniowym dla całej aplikacji lub mogą one stanowić kontener dla elementów podrzędnych. Element [biblioteki](library-element-net-native.md) , z drugiej strony, jest po prostu kontenerem. Elementy podrzędne [aplikacji](application-element-net-native.md) i [biblioteki](library-element-net-native.md) definiują typy, metody, pola, właściwości i zdarzenia, które są dostępne do odbicia.

Aby uzyskać informacje referencyjne, wybierz elementy z następującej struktury lub zobacz [elementy dyrektywy środowiska uruchomieniowego](runtime-directive-elements.md). W poniższej hierarchii wielokropek oznacza strukturę cykliczną. Informacje w nawiasach wskazują, czy ten element jest opcjonalny, czy wymagany, a jeśli jest używany, ile wystąpień (jeden lub wiele) jest dozwolonych.

- [Dyrektywy](directives-element-net-native.md) [1:1]
  - [Aplikacja](application-element-net-native.md) [0:1]
    - [Zestaw](assembly-element-net-native.md) [0: M]
      - [Przestrzeń nazw](namespace-element-net-native.md) [0: M]. . .
      - [Typ](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
    - [Przestrzeń nazw](namespace-element-net-native.md) [0: M]
      - [Przestrzeń nazw](namespace-element-net-native.md) [0: M]. . .
      - [Typ](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
    - [Typ](type-element-net-native.md) [0: M]
      - [Podtypy](subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1]
      - [Typ](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
      - [AttributeImplies](attributeimplies-element-net-native.md) (zawierający typ jest atrybutem) [O:1]
      - [GenericParameter](genericparameter-element-net-native.md) [0: M]
      - [Metoda](method-element-net-native.md) [0: M]
        - [Parametr](parameter-element-net-native.md) [0: M]
        - [TypeParameter](typeparameter-element-net-native.md) [0: M]
        - [GenericParameter](genericparameter-element-net-native.md) [0: M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M]
      - [Właściwość](property-element-net-native.md) [0: M]
      - [Pole](field-element-net-native.md) [0: M]
      - [Zdarzenie](event-element-net-native.md) [0: M]
    - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]
      - [Typ](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
      - [Metoda](method-element-net-native.md) [0: M]
        - [Parametr](parameter-element-net-native.md) [0: M]
        - [TypeParameter](typeparameter-element-net-native.md) [0: M]
        - [GenericParameter](genericparameter-element-net-native.md) [0: M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M]
      - [Właściwość](property-element-net-native.md) [0: M]
      - [Pole](field-element-net-native.md) [0: M]
      - [Zdarzenie](event-element-net-native.md) [0: M]
  - [Biblioteka](library-element-net-native.md) [0: M]
    - [Zestaw](assembly-element-net-native.md) [0: M]
      - [Przestrzeń nazw](namespace-element-net-native.md) [0: M]. . .
      - [Typ](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
    - [Przestrzeń nazw](namespace-element-net-native.md) [0: M]
      - [Przestrzeń nazw](namespace-element-net-native.md) [0: M]. . .
      - [Typ](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
    - [Typ](type-element-net-native.md) [0: M]
      - [Podtypy](subtypes-element-net-native.md) (podklasy typu zawierającego) [O:1]
      - [Typ](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
      - [AttributeImplies](attributeimplies-element-net-native.md) (zawierający typ jest atrybutem) [O:1]
      - [GenericParameter](genericparameter-element-net-native.md) [0: M]
      - [Metoda](method-element-net-native.md) [0: M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M]
      - [Właściwość](property-element-net-native.md) [0: M]
      - [Pole](field-element-net-native.md) [0: M]
      - [Zdarzenie](event-element-net-native.md) [0: M]
    - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]
      - [Typ](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (skonstruowany typ ogólny) [0: M]. . .
      - [Metoda](method-element-net-native.md) [0: M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (konstrukcja metody ogólnej) [0: M]
      - [Właściwość](property-element-net-native.md) [0: M]
      - [Pole](field-element-net-native.md) [0: M]
      - [Zdarzenie](event-element-net-native.md) [0: M]

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

Zasady, które mogą być wyrażone przez [aplikację](application-element-net-native.md), [zestaw](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [przestrzeń nazw](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)i elementy [typu](type-element-net-native.md) , różnią się od zasad, które mogą być wyrażone dla poszczególnych członków (przez [metodę](method-element-net-native.md), [Właściwość](property-element-net-native.md), [pole](field-element-net-native.md)i elementy [zdarzenia](event-element-net-native.md) ).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Określanie zasad dla zestawów, przestrzeni nazw i typów

Elementy [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [podtyp](subtypes-element-net-native.md)i [Type](type-element-net-native.md) obsługują następujące typy zasad:

- `Activate`. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, aby umożliwić aktywację wystąpień.

- `Browse`. Steruje wykonywaniem zapytań dotyczących informacji o elementach programu, ale nie umożliwia dostępu do środowiska uruchomieniowego.

- `Dynamic`. Kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne.

- `Serialize`. Kontroluje dostęp środowiska uruchomieniowego do konstruktorów, pól i właściwości, aby umożliwić Serializowanie i Serializowanie wystąpień typu przez biblioteki innych firm, takie jak serializator JSON Newtonsoft.

- `DataContractSerializer`. Kontroluje zasady dla serializacji korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.

- `DataContractJsonSerializer`. Kontroluje zasady dla serializacji JSON korzystającej z klasy <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.

- `XmlSerializer`. Kontroluje zasady dla serializacji XML, która używa klasy <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.

- `MarshalObject`. Kontroluje zasady dotyczące organizowania typów odwołań do WinRT i COM.

- `MarshalDelegate`. Steruje zasadami organizowania typów delegatów jako wskaźników funkcji do kodu natywnego.

- `MarshalStructure` . Steruje zasadami organizowania struktur w kodzie natywnym.

Ustawienia skojarzone z tymi typami zasad są następujące:

- `All`. Włącz zasady dla wszystkich typów i elementów członkowskich, które nie są usuwane przez łańcuch narzędzi.

- `Auto`. Użyj zachowania domyślnego. (Nieokreślanie zasad jest równoznaczne z ustawieniem zasad do `Auto`, chyba że te zasady zostaną zastąpione, na przykład przez element nadrzędny).

- `Excluded`. Wyłącz zasady dla elementu program.

- `Public`. Włącz zasady dla typów publicznych lub członków, chyba że łańcuch narzędzi nie ustali, że element członkowski jest niepotrzebny i usuwa go. (W tym drugim przypadku należy użyć `Required Public`, aby upewnić się, że element członkowski jest przechowywany i ma możliwości odbicia).

- `PublicAndInternal`. Włącz zasady dla typów publicznych i wewnętrznych lub członków, jeśli łańcuch narzędzi nie zostanie usunięty.

- `Required Public`. Należy wymagać łańcucha narzędzi, aby zachować publiczne typy i członków, niezależnie od tego, czy są one używane, i włączyć dla nich zasady.

- `Required PublicAndInternal`. Wymagaj, aby łańcuch narzędzi zachował typy publiczne i wewnętrzne oraz członków, niezależnie od tego, czy są one używane, i Włącz dla nich zasady.

- `Required All`. Wymagaj łańcucha narzędzi, aby zachować wszystkie typy i członków, niezależnie od tego, czy są one używane, i Włącz dla nich zasady.

Na przykład następujące pliki dyrektywy środowiska uruchomieniowego definiują zasady dla wszystkich typów i elementów członkowskich w zestawie DataClasses. dll. Umożliwia odbicie dla serializacji wszystkich właściwości publicznych, umożliwia przeglądanie dla wszystkich typów i elementów członkowskich typu, umożliwia aktywację dla wszystkich typów (z powodu `Dynamic` atrybutu) i umożliwia odbicie dla wszystkich typów i członków publicznych.

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

- `Browse`-kontroluje wykonywanie zapytań dotyczących informacji o tym elemencie członkowskim, ale nie umożliwia dostępu do środowiska uruchomieniowego.

- `Dynamic` — kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne. Steruje także wykonywaniem zapytań dotyczących informacji o typie zawierającym.

- `Serialize` — kontroluje dostęp środowiska uruchomieniowego do elementu członkowskiego, aby umożliwić serializacji i deserializacji wystąpień typu przez biblioteki, takie jak serializator JSON Newtonsoft. Te zasady można stosować do konstruktorów, pól i właściwości.

Elementy [Method](method-element-net-native.md) i [Event](event-element-net-native.md) obsługują następujące typy zasad:

- `Browse`-kontroluje zapytania o informacje dotyczące tego elementu członkowskiego, ale nie włącza żadnego dostępu do środowiska uruchomieniowego.

- `Dynamic` — kontroluje dostęp środowiska uruchomieniowego do wszystkich elementów członkowskich typu, takich jak konstruktory, metody, pola, właściwości i zdarzenia, aby umożliwić programowanie dynamiczne. Steruje także wykonywaniem zapytań dotyczących informacji o typie zawierającym.

 Ustawienia skojarzone z tymi typami zasad są następujące:

- `Auto` — Użyj zachowania domyślnego. (Nieokreślanie zasad jest równoznaczne z ustawieniem tych zasad do `Auto`, chyba że coś zastąpi go).

- `Excluded` — nigdy nie dołączaj metadanych dla elementu członkowskiego.

- `Included` — Włącz zasady, jeśli typ nadrzędny jest obecny w danych wyjściowych.

- `Required` — Wymagaj łańcucha narzędzi, aby zachować ten element członkowski nawet wtedy, gdy jest nieużywany, i Włącz dla niego zasady.

## <a name="runtime-directives-file-semantics"></a>Semantyka plików dyrektyw środowiska uruchomieniowego

Zasady można definiować jednocześnie dla elementów wyższego poziomu i niższego poziomu. Na przykład można zdefiniować zasady dla zestawu i dla niektórych typów zawartych w tym zestawie. Jeśli określony element niższego poziomu nie jest reprezentowany, dziedziczy on zasady jego elementu nadrzędnego. Na przykład jeśli element `Assembly` jest obecny, ale `Type` elementy nie są, zasady określone w elemencie `Assembly` mają zastosowanie do każdego typu w zestawie. Wiele elementów może również stosować zasady do tego samego elementu programu. Na przykład oddzielne elementy [zestawu](assembly-element-net-native.md) mogą definiować ten sam element zasad dla tego samego zestawu inaczej. W poniższych sekcjach wyjaśniono, w jaki sposób zasady dla określonego typu są rozwiązywane w tych przypadkach.

[Typ](type-element-net-native.md) lub element [metody](method-element-net-native.md) typu ogólnego lub metody stosuje zasady do wszystkich wystąpień, które nie mają własnych zasad. Na przykład element `Type`, który określa zasady dla <xref:System.Collections.Generic.List%601>, ma zastosowanie do wszystkich skonstruowanych wystąpień tego typu ogólnego, chyba że zostanie on zastąpiony dla określonego konstruowanego typu ogólnego (takiego jak `List<Int32>`) przez element `TypeInstantiation`. W przeciwnym razie elementy definiują zasady dla elementu programu o nazwie.

Gdy element jest niejednoznaczny, aparat szuka pasujących elementów i jeśli znajdzie dokładne dopasowanie, użyje go. Jeśli znajdzie wiele dopasowań, pojawi się ostrzeżenie lub błąd.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Jeśli dwie dyrektywy stosują zasady do tego samego elementu programu

Jeśli dwa elementy w różnych dyrektywach środowiska uruchomieniowego próbują ustawić ten sam typ zasad dla tego samego elementu programu (na przykład zestawu lub typu) do różnych wartości, konflikt zostanie rozwiązany w następujący sposób:

1. Jeśli element `Excluded` jest obecny, ma pierwszeństwo.

2. `Required` ma pierwszeństwo przed nie `Required`.

3. `All` ma pierwszeństwo przed `PublicAndInternal`, które ma pierwszeństwo przed `Public`.

4. Każde ustawienie jawne ma pierwszeństwo przed `Auto`.

Na przykład, jeśli pojedynczy projekt zawiera następujące dwa pliki dyrektywy środowiska uruchomieniowego, zasady serializacji dla klas DataClasses. dll są ustawione na `Required Public` i `All`. W takim przypadku zasady serializacji zostaną rozpoznane jako `Required All`.

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

Elementy podrzędne przesłaniają elementy nadrzędne, w tym ustawienie `Excluded`. Zastępowanie jest głównym powodem, który ma być określony `Auto`.

W poniższym przykładzie ustawienie zasad serializacji dla wszystkiego w `DataClasses`, które nie znajduje się w `DataClasses.ViewModels` byłoby `Required Public`, a wszystko to w `DataClasses` i `DataClasses.ViewModels` będzie `All`.

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

W poniższym przykładzie `Dictionary<int,int>` są przypisane zasady `Browse` tylko wtedy, gdy silnik ma kolejną przyczynę, aby nadać mu zasady `Browse` (w przeciwnym razie będzie to zachowanie domyślne); każde inne wystąpienie <xref:System.Collections.Generic.Dictionary%602> będzie miało wszystkie jego członków umożliwia przeglądania.

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

Zastosowanie zasad `Browse` do typu wiąże się z następującymi zmianami zasad:

- Typ podstawowy typu jest oznaczony przy użyciu zasad `Browse`.

- Jeśli typ jest ogólnym wystąpieniem, nieznajdująca się w jego wystąpieniu wersja typu jest oznaczona za pomocą zasad `Browse`.

- Jeśli typ jest delegatem, Metoda `Invoke` typu jest oznaczona przy użyciu zasad `Dynamic`.

- Każdy interfejs typu jest oznaczony przy użyciu zasad `Browse`.

- Typ każdego atrybutu zastosowanego do typu jest oznaczony przy użyciu zasad `Browse`.

- Jeśli typ jest ogólny, każdy typ ograniczenia jest oznaczony przy użyciu zasad `Browse`.

- Jeśli typ jest ogólny, typy, w których tworzone jest wystąpienie typu są oznaczone przy użyciu zasad `Browse`.

Zastosowanie zasad `Browse` do metody obejmuje następujące zmiany zasad:

- Każdy typ parametru metody jest oznaczony przy użyciu zasad `Browse`.

- Zwracany typ metody jest oznaczony przy użyciu zasad `Browse`.

- Typ zawierający metodę jest oznaczony przy użyciu zasad `Browse`.

- Jeśli metoda jest wystąpieniem metody generycznej, Metoda niebędąca wystąpieniem jest oznaczona za pomocą zasad `Browse`.

- Typ każdego atrybutu zastosowanego do metody jest oznaczony przy użyciu zasad `Browse`.

- Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczony przy użyciu zasad `Browse`.

- Jeśli metoda jest ogólna, typy, w których tworzone jest wystąpienie metody są oznaczone przy użyciu zasad `Browse`.

Zastosowanie zasad `Browse` do pola obejmuje następujące zmiany zasad:

- Typ każdego atrybutu zastosowanego do pola jest oznaczony przy użyciu zasad `Browse`.

- Typ pola jest oznaczony przy użyciu zasad `Browse`.

- Typ, do którego należy pole, jest oznaczony przy użyciu zasad `Browse`.

#### <a name="the-effect-of-dynamic-policy"></a>Efekt zasad dynamicznych

Zastosowanie zasad `Dynamic` do typu wiąże się z następującymi zmianami zasad:

- Typ podstawowy typu jest oznaczony przy użyciu zasad `Dynamic`.

- Jeśli typ jest ogólnym wystąpieniem, nieznajdująca się w jego wystąpieniu wersja typu jest oznaczona za pomocą zasad `Dynamic`.

- Jeśli typ jest typem delegata, Metoda `Invoke` typu jest oznaczona przy użyciu zasad `Dynamic`.

- Każdy interfejs typu jest oznaczony przy użyciu zasad `Browse`.

- Typ każdego atrybutu zastosowanego do typu jest oznaczony przy użyciu zasad `Browse`.

- Jeśli typ jest ogólny, każdy typ ograniczenia jest oznaczony przy użyciu zasad `Browse`.

- Jeśli typ jest ogólny, typy, w których tworzone jest wystąpienie typu są oznaczone przy użyciu zasad `Browse`.

Zastosowanie zasad `Dynamic` do metody obejmuje następujące zmiany zasad:

- Każdy typ parametru metody jest oznaczony przy użyciu zasad `Browse`.

- Zwracany typ metody jest oznaczony przy użyciu zasad `Dynamic`.

- Typ zawierający metodę jest oznaczony przy użyciu zasad `Dynamic`.

- Jeśli metoda jest wystąpieniem metody generycznej, Metoda niebędąca wystąpieniem jest oznaczona za pomocą zasad `Browse`.

- Typ każdego atrybutu zastosowanego do metody jest oznaczony przy użyciu zasad `Browse`.

- Jeśli metoda jest ogólna, każdy typ ograniczenia jest oznaczony przy użyciu zasad `Browse`.

- Jeśli metoda jest ogólna, typy, w których tworzone jest wystąpienie metody są oznaczone przy użyciu zasad `Browse`.

- Metoda może być wywoływana przez `MethodInfo.Invoke`, a tworzenie delegatów będzie możliwe przez <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.

Zastosowanie zasad `Dynamic` do pola obejmuje następujące zmiany zasad:

- Typ każdego atrybutu zastosowanego do pola jest oznaczony przy użyciu zasad `Browse`.

- Typ pola jest oznaczony przy użyciu zasad `Dynamic`.

- Typ, do którego należy pole, jest oznaczony przy użyciu zasad `Dynamic`.

#### <a name="the-effect-of-activation-policy"></a>Efekt zasad aktywacji

Zastosowanie zasad aktywacji do typu wiąże się z następującymi zmianami zasad:

- Jeśli typ jest ogólnym wystąpieniem, nieznajdująca się w jego wystąpieniu wersja typu jest oznaczona za pomocą zasad `Browse`.

- Jeśli typ jest typem delegata, Metoda `Invoke` typu jest oznaczona przy użyciu zasad `Dynamic`.

- Konstruktory typu są oznaczone przy użyciu zasad `Activation`.

Zastosowanie zasad `Activation` do metody obejmuje następujące zmiany zasad:

- Konstruktor może być wywoływany przez metody <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> i <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>. W przypadku metod zasady `Activation` mają wpływ tylko na konstruktory.

Zastosowanie zasad `Activation` do pola nie ma żadnego wpływu.

#### <a name="the-effect-of-serialize-policy"></a>Efekt serializacji zasad

Zasady `Serialize` umożliwiają korzystanie z typowych serializatorów opartych na odbiciach. Jednak ze względu na to, że wzorce dostępu do odbicia dla serializatorów firm innych niż Microsoft nie są znane firmie Microsoft, te zasady mogą nie być całkowicie skuteczne.

Zastosowanie zasad `Serialize` do typu wiąże się z następującymi zmianami zasad:

- Typ podstawowy typu jest oznaczony przy użyciu zasad `Serialize`.

- Jeśli typ jest ogólnym wystąpieniem, nieznajdująca się w jego wystąpieniu wersja typu jest oznaczona za pomocą zasad `Browse`.

- Jeśli typ jest typem delegata, Metoda `Invoke` typu jest oznaczona przy użyciu zasad `Dynamic`.

- Jeśli typ jest wyliczeniem, tablica typu jest oznaczona za pomocą zasad `Serialize`.

- Jeśli typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` jest oznaczony przy użyciu zasad `Serialize`.

- Jeśli typ to <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>lub <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` i <xref:System.Collections.Generic.List%601> oznaczone zasadami `Serialize`., ale żaden element członkowski typu interfejsu nie jest oznaczony przy użyciu zasad `Serialize`.

- Jeśli typ jest <xref:System.Collections.Generic.List%601>, żadne elementy członkowskie tego typu nie są oznaczone przy użyciu zasad `Serialize`ymi.

- Jeśli typ jest <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> zostanie oznaczony przy użyciu zasad `Serialize`. ale żadne elementy członkowskie tego typu nie są oznaczone za pomocą zasad `Serialize`.

- Jeśli typ jest <xref:System.Collections.Generic.Dictionary%602>, żadne elementy członkowskie tego typu nie są oznaczone przy użyciu zasad `Serialize`ymi.

- Jeśli typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` i `TValue` są oznaczone przy użyciu zasad `Serialize`.

- Każdy Konstruktor, każdy akcesor właściwości i każde pole jest oznaczone za pomocą zasad `Serialize`.

Zastosowanie zasad `Serialize` do metody obejmuje następujące zmiany zasad:

- Typ zawierający jest oznaczony przy użyciu zasad `Serialize`.

- Zwracany typ metody jest oznaczony przy użyciu zasad `Serialize`.

Zastosowanie zasad `Serialize` do pola obejmuje następujące zmiany zasad:

- Typ zawierający jest oznaczony przy użyciu zasad `Serialize`.

- Typ pola jest oznaczony przy użyciu zasad `Serialize`.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>Wpływ zasad XmlSerializer, DataContractSerializer i Klasa DataContractJsonSerializer

W przeciwieństwie do zasad `Serialize`, które są przeznaczone dla serializatorów opartych na odbiciach, zasady <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> są używane do włączania zestawu serializatorów znanych do łańcucha narzędzi .NET Native. Te serializacji nie są implementowane przy użyciu odbicia, ale zestaw typów, które mogą być serializowane w czasie wykonywania, jest określany w podobny sposób, jak typy, które są odzwierciedlane.

Zastosowanie jednej z tych zasad do typu umożliwia serializacji typu przy użyciu pasującego serializatora. Ponadto wszelkie typy, które aparat serializacji może statycznie określić, ponieważ wymaganie serializacji również będzie możliwe do serializacji.

Te zasady nie mają wpływu na metody lub pola.

Aby uzyskać więcej informacji, zobacz sekcję "różnice w Serializatorach" w temacie [Migrowanie aplikacji ze sklepu Windows do .NET Native](migrating-your-windows-store-app-to-net-native.md).

## <a name="see-also"></a>Zobacz także

- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Odbicie i architektura .NET Native](reflection-and-net-native.md)

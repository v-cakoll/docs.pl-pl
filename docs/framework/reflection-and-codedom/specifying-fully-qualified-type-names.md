---
title: Określanie w pełni kwalifikowanych nazw typów
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc8395492992c22da3c635f0de010516127f9be4
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612865"
---
# <a name="specifying-fully-qualified-type-names"></a>Określanie w pełni kwalifikowanych nazw typów

Należy określić nazwy typów, które mają prawidłowe dane wejściowe do różnych operacji odbicia. W pełni kwalifikowaną nazwę typu składa się z specyfikacja nazwy zestawu, specyfikacji przestrzeni nazw i nazwę typu. Specyfikacje nazwy typu są używane przez metody takie jak <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, i <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.

## <a name="grammar-for-type-names"></a>Gramatyka dla nazwy typów

 Gramatyka definiuje składni języków formalnych. Poniższa tabela zawiera listę leksykalne reguły, które opisują rozpoznawanie prawidłowych danych wejściowych. Terminali (te elementy, które nie są dodatkowo obniżaniu) są wyświetlane w wielkie litery. Symboli nieterminalnych (te elementy, które są dodatkowo obniżaniu) są wyświetlane w ciągach znaków, jak i pojedynczo cudzysłowach, ale apostrof (') nie jest częścią składni sam. Znaku kreski pionowej (&#124;) oznacza reguły, które mają reguły podrzędne.

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a>Określania znaków specjalnych

W nazwie typu identyfikator jest Dowolna prawidłowa nazwa określona w zasadach języka.

Użyj ukośnik odwrotny (\\) jako znak ucieczki, aby oddzielić następujące generatory kodów, gdy jest używana jako część IDENTYFIKATORA.

|Token|Znaczenie|
|-----------|-------------|
|\\,|Separator zestawu.|
|\\+|Separator typu zagnieżdżonego.|
|\\&|Typ odwołania.|
|\\*|Typ wskaźnika.|
|\\[|Ogranicznik wymiaru tablicy.|
|\\]|Ogranicznik wymiaru tablicy.|
|\\.|Użyj ukośnik odwrotny przed kropką, tylko wtedy, gdy kropka jest używana w specyfikacji tablicy. Okresy w NamespaceSpec nie przyjmują ukośnik odwrotny.|
|\\\|Ukośnik odwrotny w razie jako ciąg literału.|

Należy pamiętać, że TypeSpec wszystkie składniki z wyjątkiem AssemblyNameSpec, spacje są istotne. W AssemblyNameSpec spacje przed separatorem ',' są istotne, ale spacje po separatorze ',' są ignorowane.

Odbicie klasy takie jak <xref:System.Type.FullName%2A?displayProperty=nameWithType>, wróć zniekształcone nazwy, nazwa zwróconego mogą być używane w wywołaniu <xref:System.Type.GetType%2A>, jak w `MyType.GetType(myType.FullName)`.

Na przykład może być w pełni kwalifikowana nazwa typu `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.

Jeśli przestrzeń nazw `Ozzy.Out+Back`, a następnie znak plus musi być poprzedzony znakiem ukośnika odwrotnego. W przeciwnym razie analizatora będzie zinterpretuje ją jako separator zagnieżdżenia. Odbicie emituje ten ciąg w kodowaniu `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.

## <a name="specifying-assembly-names"></a>Określanie nazwy zestawów

Minimalnych wymaganych informacji w specyfikacja nazwy zestawu jest tekstowa Nazwa zestawu (identyfikator). Możesz wykonać identyfikator listę rozdzielonych przecinkami pary właściwość/wartość, zgodnie z opisem w poniższej tabeli. Nazewnictwa identyfikatorów należy stosować reguły nazewnictwa plików. Identyfikator jest rozróżniana wielkość liter.

|Nazwa właściwości|Opis|Dopuszczalne wartości|
|-------------------|-----------------|----------------------|
|**Wersja**|Numer wersji zestawu|*Główna.pomocnicza.kompilacja.poprawka*, gdzie *głównych*, *pomocnicza*, *kompilacji*, i *poprawki* są liczbami całkowitymi od 0 i 65535 (włącznie).|
|**PublicKey**|Klucz publiczny pełnej|Wartość klucza pełnej publicznego w formacie szesnastkowym ciągu. Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.|
|**PublicKeyToken**|Token klucza publicznego (8-bajtowych skrót klucza publicznego pełnej)|Wartość tokenu klucza publicznego w formacie szesnastkowym ciągu. Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.|
|**Kultury**|Język zestawu|Kultura zestawu w formacie RFC 1766 lub "węgla" zestawy niezależny od języka (nonsatellite).|
|**Custom**|Niestandardowe duży obiekt binarny (BLOB). Obecnie jest on używany tylko w zestawów generowanych przez [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|Niestandardowy ciąg jest używany przez narzędzie Native Image Generator, by powiadomić pamięci podręcznej zestawów, czy zestaw instalowany jest obraz macierzysty i dlatego ma być zainstalowany w pamięci podręcznej obrazów natywnych. Skrót ciągu zap.|

W poniższym przykładzie przedstawiono **AssemblyName** po prostu nazwanego zestawu przy użyciu domyślnej kultury.

```csharp
com.microsoft.crypto, Culture=""
```

Poniższy przykład przedstawia w pełni określone odwołanie dla zestawu o silnej nazwie z kulturą "en".

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

W poniższych przykładach każdego pokazano częściowo określoną **AssemblyName**, które mogą zostać zrealizowane przez silne lub po prostu nazwanego zestawu.

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

W poniższych przykładach każdego pokazano częściowo określoną **AssemblyName**, muszą być spełnione, po prostu nazwanego zestawu.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

W poniższych przykładach każdego pokazano częściowo określoną **AssemblyName**, muszą być spełnione przez zestaw o silnej nazwie.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a>Określanie typów ogólnych

SimpleTypeSpec\`numer reprezentuje to otwarty typ ogólny z od 1 do *n* parametrów typu genetycznego. Na przykład, można pobrać odwołania do otwarty typ ogólny listy\<T > lub zamknięty typ ogólny List\<ciągu >, użyj ``Type.GetType("System.Collections.Generic.List`1")`` można pobrać odwołania do typu ogólnego słownika\<TKey, TValue >, użyj ``Type.GetType("System.Collections.Generic.Dictionary`2")``.

## <a name="specifying-pointers"></a>Określenie wskaźników

SimpleTypeSpec * reprezentuje niezarządzanym wskaźnikiem. Na przykład, aby uzyskać wskaźnik do typu MyType, użyj `Type.GetType("MyType*")`. Aby uzyskać wskaźnik do wskaźnika do typu MyType, użyj `Type.GetType("MyType**")`.

## <a name="specifying-references"></a>Określanie odwołania

SimpleTypeSpec & reprezentuje zarządzane wskaźnika lub odwołania. Na przykład, aby uzyskać odwołanie do typu MyType, należy użyć `Type.GetType("MyType &")`. Należy pamiętać, że w przeciwieństwie do wskaźników, odwołań są ograniczone do jednego poziomu.

## <a name="specifying-arrays"></a>Określanie tablic

W gramatyka BNF ReflectionEmitDimension ma zastosowanie tylko w definicjach niekompletnego typu pobrany przy użyciu <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>. Definicje niekompletnego typu <xref:System.Reflection.Emit.TypeBuilder> tworzony przy użyciu obiektów <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale na którym <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nie została wywołana. ReflectionDimension może służyć do pobrania żadnych definicji typu, który został wykonany, to znaczy, typ, który został załadowany.

Tablice są dostępne w odbiciu, określając rangę tablicy:

- `Type.GetType("MyArray[]")` pobiera tablicy jednowymiarowej, za pomocą 0 dolną granicę.

- `Type.GetType("MyArray[*]")` pobiera tablicy jednowymiarowej, za pomocą nieznany dolną granicę.
- `Type.GetType("MyArray[][]")` Pobiera tablicę dwuwymiarową tablicę.

- `Type.GetType("MyArray[*,*]")` i `Type.GetType("MyArray[,]")` pobiera prostokątnej dwuwymiarowej tablicy przy użyciu nieznanego dolne granice.

Należy pamiętać, że z punktu widzenia środowiska uruchomieniowego, `MyArray[] != MyArray[*]`, ale dla tablic wielowymiarowych dwóch notacji są równoważne. Oznacza to, że `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` daje w wyniku **true**.

Aby uzyskać **ModuleBuilder.GetType**, `MyArray[0..5]` wskazuje tablicy jednowymiarowej, o rozmiarze 6, niższe powiązane 0. `MyArray[4…]` Wskazuje tablicy jednowymiarowej, o nieznanym rozmiarze i dolnej granicy 4.

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)

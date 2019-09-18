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
ms.openlocfilehash: 656b82daffc62824ed663ea7080bd6d20cd0dadc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045819"
---
# <a name="specifying-fully-qualified-type-names"></a>Określanie w pełni kwalifikowanych nazw typów

Musisz określić nazwy typów, aby mieć prawidłowe dane wejściowe różnych operacji odbicia. W pełni kwalifikowana nazwa typu zawiera specyfikację nazwy zestawu, specyfikację przestrzeni nazw i nazwę typu. Specyfikacje nazw typów są używane przez metody takie jak <xref:System.Type.GetType%2A?displayProperty=nameWithType> <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>,, i <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.

## <a name="grammar-for-type-names"></a>Gramatyka nazw typów

 Gramatyka definiuje składnię języków formalnych. W poniższej tabeli wymieniono reguły leksykalne opisujące sposób rozpoznawania prawidłowych danych wejściowych. W przypadku terminali (te elementy, które nie są jeszcze możliwe do zredukowania), są wyświetlane wielkie litery. Nieterminale (te elementy, które są dalsze możliwe do zredukowania) są wyświetlane w postaci ciągów z rozróżnianą wielkością liter lub z pojedynczą cudzysłowem, ale pojedynczy cudzysłów (') nie jest częścią samej składni. Znak potoku (&#124;) oznacza reguły mające reguły subrules.

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

## <a name="specifying-special-characters"></a>Określanie znaków specjalnych

W nazwie typu identyfikator to dowolna prawidłowa nazwa określona przez reguły języka.

Użyj ukośnika odwrotnego\\() jako znaku ucieczki, aby oddzielić następujące tokeny, gdy są używane jako część identyfikatora.

|Token|Znaczenie|
|-----------|-------------|
|\\,|Separator zestawu.|
|\\+|Zagnieżdżony Separator typu.|
|\\&|Typ referencyjny.|
|\\*|Typ wskaźnika.|
|\\[|Ogranicznik wymiaru tablicy.|
|\\]|Ogranicznik wymiaru tablicy.|
|\\.|Użyj ukośnika odwrotnego przed kropką, tylko jeśli okres jest używany w specyfikacji tablicy. Okresy w NamespaceSpec nie przyjmują ukośnika odwrotnego.|
|\\\|Ukośnik odwrotny, gdy jest wymagany jako literał ciągu.|

Należy pamiętać, że we wszystkich składnikach TypeSpec z wyjątkiem AssemblyNameSpec, spacje są istotne. W AssemblyNameSpec, spacje przed separatorem ', ' są istotne, ale spacje po separatorze ', ' są ignorowane.

Klasy odbicia, takie <xref:System.Type.FullName%2A?displayProperty=nameWithType>jak, zwracają nazwę zniekształcona, aby można było użyć zwracanej nazwy w wywołaniu do <xref:System.Type.GetType%2A>, jako w `MyType.GetType(myType.FullName)`.

Na przykład w pełni kwalifikowana nazwa dla typu może być `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.

Jeśli przestrzeń nazw była `Ozzy.Out+Back`, znak plus musi być poprzedzony ukośnikiem odwrotnym. W przeciwnym razie Analizator interpretuje go jako separator zagnieżdżenia. Odbicie emituje ten ciąg `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`jako.

## <a name="specifying-assembly-names"></a>Określanie nazw zestawów

Minimalnymi informacjami wymaganymi w specyfikacji nazwy zestawu jest nazwa tekstowa (identyfikator) zestawu. Identyfikator można obsłużyć rozdzielaną przecinkami listą par właściwości/wartości, zgodnie z opisem w poniższej tabeli. Nazewnictwo identyfikatorów powinno być zgodne z regułami dotyczącymi nazewnictwa plików. W IDENTYFIKATORze nie jest rozróżniana wielkość liter.

|Nazwa właściwości|Opis|Dozwolone wartości|
|-------------------|-----------------|----------------------|
|**Wersja**|Numer wersji zestawu|*Główna. pomocnicza. kompilacja. poprawka*, gdzie *główna*, *pomocnicza*, *kompilacja*i *poprawka* są liczbami całkowitymi z zakresu od 0 do 65535 włącznie.|
|**PublicKey**|Pełny klucz publiczny|Wartość ciągu pełnego klucza publicznego w formacie szesnastkowym. Określ odwołanie o wartości null (**Nothing** w Visual Basic), aby jawnie wskazać prywatny zestaw.|
|**PublicKeyToken**|Token klucza publicznego (skrót 8-bajtowy pełnego klucza publicznego)|Wartość ciągu tokenu klucza publicznego w formacie szesnastkowym. Określ odwołanie o wartości null (**Nothing** w Visual Basic), aby jawnie wskazać prywatny zestaw.|
|**Dziedzinie**|Kultura zestawu|Kultura zestawu w formacie RFC-1766 lub "neutralna" dla zestawów niezależnych od języka (niesatelity).|
|**Custom**|Niestandardowy duży obiekt binarny (BLOB). Jest to obecnie używane tylko w zestawach wygenerowanych przez [Generator obrazu natywnego (Ngen)](../tools/ngen-exe-native-image-generator.md).|Niestandardowy ciąg używany przez Narzędzie Generator obrazu macierzystego do powiadamiania pamięci podręcznej zestawów, że instalowany zestaw jest obrazem natywnym i dlatego jest instalowany w pamięci podręcznej obrazów natywnych. Nazywana również ciągiem zap.|

W poniższym przykładzie pokazano element **AssemblyName** dla jednoplikowego zestawu z domyślną kulturą.

```csharp
com.microsoft.crypto, Culture=""
```

W poniższym przykładzie pokazano w pełni określone odwołanie do zestawu o silnej nazwie z kulturą "pl".

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

W poniższych przykładach pokazano częściowo określony element **AssemblyName**, który może być spełniony przez silną lub jednoplikowy zestaw.

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

Poniższe przykłady pokazują częściowo określony element **AssemblyName**, który musi być spełniony przez zestaw po prostu o nazwie.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

Poniższe przykłady pokazują częściowo określony element **AssemblyName**, który musi być spełniony przez silnie nazwany zestaw.

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a>Określanie typów ogólnych

SimpleTypeSpec\`numer reprezentuje otwarty typ ogólny z od 1 do *n* parametrów typu ogólnego. Aby na przykład uzyskać odwołanie\<do listy otwartych typów ogólnych T > lub zamkniętego ciągu listy\<typów ogólnych >, użyj ``Type.GetType("System.Collections.Generic.List`1")`` , aby uzyskać odwołanie do słownika\<typu ogólnego TKey, TValue >, użyj ``Type.GetType("System.Collections.Generic.Dictionary`2")``.

## <a name="specifying-pointers"></a>Określanie wskaźników

SimpleTypeSpec * reprezentuje niezarządzany wskaźnik. Na przykład aby uzyskać wskaźnik do typu MyType, użyj `Type.GetType("MyType*")`. Aby uzyskać wskaźnik do wskaźnika do typu MyType, użyj `Type.GetType("MyType**")`.

## <a name="specifying-references"></a>Określanie odwołań

SimpleTypeSpec & reprezentuje zarządzany wskaźnik lub odwołanie. Na przykład aby uzyskać odwołanie do typu MyType, użyj `Type.GetType("MyType &")`. Należy pamiętać, że w przeciwieństwie do wskaźników, odwołania są ograniczone do jednego poziomu.

## <a name="specifying-arrays"></a>Określanie tablic

W BNF gramatyki ReflectionEmitDimension dotyczy tylko niekompletnych definicji typów pobranych przy <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>użyciu. Niekompletne definicje typów <xref:System.Reflection.Emit.TypeBuilder> są obiektami zbudowanymi przy użyciu <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> polecenia <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale nie zostały wywołane. ReflectionDimension można użyć do pobrania dowolnej definicji typu, która została ukończona, czyli typu, który został załadowany.

Tablice są dostępne w odbiciu, określając rangę tablicy:

- `Type.GetType("MyArray[]")`Pobiera tablicę o pojedynczym wymiarze z dolną granicą 0.

- `Type.GetType("MyArray[*]")`Pobiera tablicę o pojedynczym wymiarze z nieznanym dolnym granicą.
- `Type.GetType("MyArray[][]")`Pobiera tablicę dwuwymiarową tablicy.

- `Type.GetType("MyArray[*,*]")`i `Type.GetType("MyArray[,]")` pobiera prostokątną dwuwymiarową tablicę z nieznanymi dolnymi granicami.

Należy pamiętać, że z punktu `MyArray[] != MyArray[*]`widzenia środowiska uruchomieniowego, ale dla tablic wielowymiarowych, dwie notacji są równoważne. Oznacza to, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` że program zwraca **wartość true**.

Dla **ModuleBuilder. GetType** `MyArray[0..5]` wskazuje tablicę jednowymiarową z rozmiarem 6, dolną granicą 0. `MyArray[4…]`wskazuje tablicę z jednym wymiarem o nieznanym rozmiarze i dolną granicę 4.

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [Wyświetlanie informacji o typie](viewing-type-information.md)

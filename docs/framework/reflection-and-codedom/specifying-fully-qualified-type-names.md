---
title: Określanie w pełni kwalifikowanych nazw typów
ms.date: 03/14/2018
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
ms.openlocfilehash: 437bbb7a1645c0ab13da33e57c1e70b5ec98984c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="specifying-fully-qualified-type-names"></a>Określanie w pełni kwalifikowanych nazw typów
Należy określić nazwy typów ma prawidłową wartość wejściową do różnych operacji odbicia. Nazwa FQDN typu, który składa się z specyfikacja nazwy zestawu specyfikacji przestrzeni nazw i nazwę typu. Specyfikacje nazwy typów są używane przez metody takie jak <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, i <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.  
  
## <a name="grammar-for-type-names"></a>Gramatyka dla nazw typów  
 Gramatyka definiuje składni posiadanie języków. W poniższej tabeli wymieniono leksykalne reguły, które opisują jak rozpoznać prawidłowych danych wejściowych. Terminali (tych elementów, które nie są dodatkowo możliwym do zredukowania) są wyświetlane w wielkie litery. Symboli nieterminalnych (tych elementów, które są dodatkowo możliwym do zredukowania) są wyświetlane w ciągach wielkie i małe litery, lub oddzielnie w cudzysłowie, ale apostrofu (') nie jest częścią sama składnia. Znaku kreski pionowej (&#124;) oznacza reguły, które mają reguł podrzędnych.  

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
    | ArrayTypeSpec
    | TypeName
    ;

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

## <a name="specifying-special-characters"></a>Określanie znaki specjalne  
 W nazwie typu identyfikator jest żadnych prawidłowej nazwy określane przez reguły języka.  
  
 Użyj kreska ułamkowa odwrócona (\\) jako znaku ucieczki w celu rozdzielenia następujących tokenów, gdy jest używany jako część IDENTYFIKATORA.  
  
|Token|Znaczenie|  
|-----------|-------------|  
|\\,|Separator zestawu.|  
|\\+|Separator typu zagnieżdżonego.|  
|\\&|Typ odwołania.|  
|\\*|Typ wskaźnika.|  
|\\[|Ogranicznik wymiaru tablicy.|  
|\\]|Ogranicznik wymiaru tablicy.|  
|\\.|Użyj ukośniku odwrotnym przed kropką tylko wtedy, gdy okres jest używany w specyfikacji tablicy. Kropki w NamespaceSpec nie przyjmują ukośniku odwrotnym.|  
|\\\|Ukośnik odwrotny, w razie potrzeby jako ciąg literału.|  
  
 Należy pamiętać, że we wszystkich składnikach elementu TypeSpec z wyjątkiem AssemblyNameSpec mają zastosowanie spacji. W AssemblyNameSpec mają zastosowanie spacji przed separatorem ',', ale spacje po separatorze "," są ignorowane.  
  
 Odbicie klas, takich jak <xref:System.Type.FullName%2A?displayProperty=nameWithType>, wróć nazwa zniekształcona zwrócona nazwa może być używana w wywołaniu <xref:System.Type.GetType%2A>, jak w `MyType.GetType(myType.FullName)`.  
  
 Na przykład może być w pełni kwalifikowana nazwa typu `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.  
  
 Jeśli przestrzeń nazw zostały `Ozzy.Out+Back`, a następnie znak plus musi być poprzedzony ukośnikiem. W przeciwnym razie analizator może zinterpretować go jako separator zagnieżdżenia. Odbicie emituje tego ciągu jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.  
  
## <a name="specifying-assembly-names"></a>Określanie nazwy zestawu  
 Minimalną ilość informacji w specyfikacji nazwy zestawu wymagany jest nazwą tekstową (IDENTIFIER) zestawu. Rozdzielana przecinkami lista par właściwości i wartości zgodnie z opisem w poniższej tabeli można wykonać identyfikator. Identyfikator nazwy należy stosować reguły nazewnictwa plików. Identyfikator jest rozróżniana wielkość liter.  
  
|Nazwa właściwości|Opis|Dopuszczalne wartości|  
|-------------------|-----------------|----------------------|  
|**Wersja**|Numer wersji zestawu|*Główna.pomocnicza.kompilacja.poprawka*, gdzie *głównych*, *pomocnicza*, *kompilacji*, i *poprawki* są liczbami całkowitymi od 0 i 65535 włącznie.|  
|**PublicKey**|Klucz publiczny pełnej|Wartość pełnej publiczny klucz w formacie szesnastkowym ciągu. Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.|  
|**PublicKeyToken**|Token klucza publicznego (8-bajtowych skrótu klucza publicznego pełna)|Wartość tokenu klucza publicznego w formacie szesnastkowym ciągu. Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.|  
|**Kultury**|Kultura zestawu|Kultura zestawu w formacie RFC 1766 lub "neutralne" dla zestawów niezależny od języka (nonsatellite).|  
|**Niestandardowy**|Niestandardowe dużego obiektu binarnego (BLOB). To jest aktualnie używana tylko zestawów generowanych przez [Generator obrazu natywnego (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|Niestandardowy ciąg używany przez narzędzie Generator obrazu natywnego do powiadamiania pamięci podręcznej zestawów zestawu instalowany jest obrazu macierzystego czy w związku z tym ma zostać zainstalowany w pamięci podręcznej obrazów natywnych. Skrót ciągu zap.|  
  
 W poniższym przykładzie przedstawiono **AssemblyName** po prostu nazwane zestawu z domyślną kulturę.  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 W poniższym przykładzie przedstawiono pełni podane odwołanie do zestawu o silnej nazwie z kulturą "en".  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, który może zostać wykonane przez silne lub po prostu nazwane zestawu.  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, muszą być spełnione przez po prostu nazwany zestaw.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, muszą być spełnione przez zestaw o silnej nazwie.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a>Określenie wskaźników  
 SimpleTypeSpec * reprezentuje niezarządzanego wskaźnika. Na przykład otrzymywać wskaźnik do typu Mojtyp, należy użyć `Type.GetType("MyType*")`. Aby otrzymywać wskaźnik na wskaźnik do typu Mojtyp, należy użyć `Type.GetType("MyType**")`.  
  
## <a name="specifying-references"></a>Określanie odwołań  
 SimpleTypeSpec & reprezentuje zarządzanych wskaźnik lub odwołanie. Na przykład, aby pobrać odwołanie do typu Mojtyp, należy użyć `Type.GetType("MyType &")`. Należy pamiętać, że w przeciwieństwie do wskaźników, odwołania mogą zawierać maksymalnie jeden poziom.  
  
## <a name="specifying-arrays"></a>Określanie tablic  
 W gramatyka BNF ReflectionEmitDimension ma zastosowanie tylko do niekompletnego typu definicje pobrany przy użyciu <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>. Definicje niekompletnego typu <xref:System.Reflection.Emit.TypeBuilder> obiekty utworzone za pomocą <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale na którym <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nie została wywołana. ReflectionDimension można pobrać żadnych definicji typu, która została zakończona, oznacza to, typu, który został załadowany.  
  
 Tablice są dostępne w odbicia, określając rangą tablicy:  
  
-   `Type.GetType("MyArray[]")` pobiera tablicy jednowymiarowej z 0 dolnej granicy.  
  
-   `Type.GetType("MyArray[*]")` pobiera tablicy jednowymiarowej z nieznanego dolnej granicy.  
  
-   `Type.GetType("MyArray[][]")` pobiera tablicy jest tablicą dwuwymiarową.  
  
-   `Type.GetType("MyArray[*,*]")` i `Type.GetType("MyArray[,]")` pobiera prostokątny tablicą dwuwymiarową z nieznanego dolne granice tablicy.  
  
 Należy pamiętać, że z punktu widzenia środowiska uruchomieniowego, `MyArray[] != MyArray[*]`, ale dla tablic wielowymiarowych są równoważne dwóch notacji. Oznacza to `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` daje w wyniku **true**.  
  
 Aby uzyskać **ModuleBuilder.GetType**, `MyArray[0..5]` wskazuje tablicy jednowymiarowej, o rozmiarze 6 niższe powiązane 0. `MyArray[4…]` Wskazuje jednowymiarowej tablicy o nieznanym rozmiarze i dolną granicę 4.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)

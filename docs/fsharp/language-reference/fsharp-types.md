---
title: Typy F#
description: Dowiedz się więcej o typach, które F# są używane F# w programie oraz o nazywaniu i opisywaniu typów.
ms.date: 05/16/2016
ms.openlocfilehash: 8f2526dce46d53a92c01c9347e1ed97681a45ecc
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425303"
---
# <a name="f-types"></a>Typy F#

W tym temacie opisano typy, które są używane F# w programie F# , i sposób ich nazywania i opisywania.

## <a name="summary-of-f-types"></a>Podsumowanie F# typów

Niektóre typy są uznawane za *typy pierwotne*, takie jak typ Boolean `bool` i całkowitych i zmiennoprzecinkowych typów różnych rozmiarów, które zawierają typy dla bajtów i znaków. Te typy są opisane w [typach pierwotnych](basic-types.md).

Inne typy, które są wbudowane w język obejmują krotki, listy, tablice, sekwencje, rekordy i związki rozłącznych. Jeśli masz doświadczenie z innymi językami .NET i uczeniem F#się, zapoznaj się z tematami dotyczącymi każdego z tych typów. Linki do dodatkowych informacji na temat tych typów znajdują się w sekcji [Tematy pokrewne](https://msdn.microsoft.com/library/#rel) tego tematu. Te F#typy charakterystyczne obsługują style programowania, które są wspólne dla języków programowania. Wiele z tych typów ma skojarzone moduły w F# bibliotece, które obsługują Typowe operacje na tych typach.

Typ funkcji zawiera informacje o typach parametrów i zwracanym typie.

.NET Framework jest źródłem typów obiektów, typów interfejsów, typów delegatów i innych. Możesz definiować własne typy obiektów tak samo jak w przypadku dowolnego innego języka .NET.

Ponadto F# kod może definiować aliasy, które są nazwanymi *skrótami*typów, które są alternatywnymi nazwami typów. Możesz użyć skrótów typu, gdy typ może ulec zmianie w przyszłości i chcesz uniknąć zmiany kodu, który zależy od typu. Lub można użyć skrótu typu jako przyjaznej nazwy dla typu, który może ułatwić odczytywanie i zrozumienie kodu.

F#oferuje przydatne typy kolekcji, które są przeznaczone do programowania funkcjonalnego. Korzystanie z tych typów kolekcji ułatwia pisanie kodu, który jest bardziej funkcjonalny w stylu. Aby uzyskać więcej informacji, zobacz [ F# typy kolekcji](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Składnia typów

W F# kodzie często trzeba napisać nazwy typów. Każdy typ ma formę składni, a te formy są używane w adnotacjach typu, deklaracjach metod abstrakcyjnych, deklaracjach delegatów, sygnaturach i innych konstrukcjach. Za każdym razem, gdy deklarujesz nową konstrukcję programu w interpreterze, interpreter wyświetla nazwę konstrukcji i składnię dla jej typu. Ta składnia może być tylko identyfikatorem typu zdefiniowanego przez użytkownika lub wbudowanym identyfikatorem, takim jak dla `int` lub `string`, ale dla bardziej złożonych typów składnia jest bardziej skomplikowana.

W poniższej tabeli przedstawiono aspekty składni typów dla F# typów.

|Typ|Składnia typu|Przykłady|
|----|-----------|--------|
|typ pierwotny|*Nazwa typu*|`int`<br /><br />`float`<br /><br />`string`|
|typ agregacji (Klasa, struktura, Unia, rekord, Wyliczenie itd.)|*Nazwa typu*|`System.DateTime`<br /><br />`Color`|
|Skrót typu|*Type-skrót-Name*|`bigint`|
|w pełni kwalifikowany typ|*przestrzenie nazw. type-name*<br /><br />lub<br /><br />*modules. type-name*<br /><br />lub<br /><br />*przestrzenie nazw. modules. type-name*|`System.IO.StreamWriter`|
|tablica|*Nazwa typu*[] lub<br /><br />Tablica *nazw typu*|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|Tablica dwuwymiarowa|*Nazwa typu*[,]|`int[,]`<br /><br />`float[,]`|
|Tablica trójwymiarowa|*type-name*[,,]|`float[,,]`|
|Spoin|*Type-Name1* &#42; *Type-NAME2* ...|Na przykład `(1,'b',3)` ma typ `int * char * int`|
|typ ogólny|*Typ-parametru* *rodzajowego-nazwa*<br /><br />lub<br /><br />*Nazwa typu ogólnego* *&lt;typu*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|Typ skonstruowany (typ ogólny, który ma podany określony argument typu)|*Typ* — *typ ogólny-nazwa*<br /><br />lub<br /><br />*Nazwa typu rodzajowego*&lt;typ- *lista argumentów typu*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|Typ funkcji, która ma jeden parametr|*parametr-type1* -&gt; *Typ zwracany*|Funkcja, która przyjmuje `int` i zwraca `string`, ma typ `int -> string`|
|Typ funkcji, która ma wiele parametrów|*parametr-type1* -&gt; *parametr-Type2* -&gt;...-&gt; *zwracanego typu*|Funkcja, która przyjmuje `int` i `float` i zwraca `string`, ma typ `int -> float -> string`|
|wyższa funkcja Order jako parametr|(*Typ funkcji*)|`List.map` typu `('a -> 'b) -> 'a list -> 'b list`|
|delegate|delegat *typu funkcji*|`delegate of unit -> int`|
|Typ elastyczny|*Nazwa typu* #|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Tematy pokrewne

|Temat|Opis|
|-----|-----------|
|[Typy pierwotne](basic-types.md)|Opisuje wbudowane typy proste, takie jak typy całkowite, typ Boolean i typy znaków.|
|[Typ jednostki](unit-type.md)|Opisuje typ `unit`, typ, który ma jedną wartość i który jest wskazywany przez (); odpowiednik `void` w C# i `Nothing` w Visual Basic.|
|[Krotki](tuples.md)|Opisuje typ krotki, typ, który składa się z skojarzonych wartości dowolnego typu zgrupowanych w parach, potrójnie, czterokrotnie itd.|
|[Opcje](options.md)|Opisuje typ opcji, typ, który może mieć wartość lub być pusty.|
|[Listy](lists.md)|Opisuje listy, które są uporządkowane, z niemodyfikowalnymi seriami wszystkich elementów tego samego typu.|
|[Tablice](arrays.md)|Opisuje tablice, które są uporządkowanymi zestawami modyfikowalnych elementów tego samego typu, które zajmują ciągły blok pamięci i o stałym rozmiarze.|
|[Sekwencje](sequences.md)|Opisuje typ sekwencji, który reprezentuje serię logiczną wartości; poszczególne wartości są obliczane tylko w razie potrzeby.|
|[Rekordy](records.md)|Opisuje typ rekordu, niewielką wartość zagregowaną nazwanych wartości.|
|[Sumy rozłączne](discriminated-unions.md)|Opisuje typ Unii rozłącznych, którego wartości mogą być jednym z zestawów możliwych typów.|
|[Funkcje](./functions/index.md)|Opisuje wartości funkcji.|
|[Klasy](classes.md)|Opisuje typ klasy, typ obiektu, który odnosi się do typu referencyjnego platformy .NET. Typy klas mogą zawierać elementy członkowskie, właściwości, zaimplementowane interfejsy i typ podstawowy.|
|[Struktury](structures.md)|Opisuje typ `struct`, typ obiektu, który odpowiada typowi wartości .NET. Typ `struct` zwykle reprezentuje mały zagregowany element danych.|
|[Interfejsy](interfaces.md)|Opisuje typy interfejsów, które reprezentują zestaw elementów członkowskich, które udostępniają pewne funkcje, ale nie zawierają danych. Typ interfejsu musi być zaimplementowany przez typ obiektu, który ma być przydatny.|
|[Delegaci](delegates.md)|Opisuje typ delegata, który reprezentuje funkcję jako obiekt.|
|[Wyliczenia](enumerations.md)|Opisuje typy wyliczeniowe, których wartości należą do zestawu nazwanych wartości.|
|[Atrybuty](attributes.md)|Opisuje atrybuty, które są używane do określania metadanych dla innego typu.|
|[Typy wyjątków](./exception-handling/exception-types.md)|Opisuje wyjątki, które określają informacje o błędzie.|

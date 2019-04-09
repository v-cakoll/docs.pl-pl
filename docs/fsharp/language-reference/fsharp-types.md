---
title: Typy F#
description: Informacje o typach, które są używane w F# i w jaki sposób F# typów o nazwie i opisem.
ms.date: 05/16/2016
ms.openlocfilehash: b48376c80b48df210bf7bc699a769d40fec60864
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193593"
---
# <a name="f-types"></a>Typy F#

W tym temacie opisano typy, które są używane w F# i w jaki sposób F# typów o nazwie i opisem.

## <a name="summary-of-f-types"></a>Podsumowanie F# typów
Niektóre typy są traktowane jako *typów pierwotnych*, takie jak typ Boolean `bool` i typów całkowitych i zmiennoprzecinkowych punkt o różnych rozmiarach, które obejmują typy bajtów i znaków. Te typy są opisane w [typów pierwotnych](primitive-types.md).

Inne typy, które są wbudowane w języku obejmują krotek, list, tablic, sekwencji, rekordy i związków wyróżniających. Jeśli masz doświadczenie z innymi językami .NET i learning F#, możesz zapoznaj się z tematami dla każdego z tych typów. Linki do szczegółowych informacji o tych typach znajdują się w [Tematy pokrewne](https://msdn.microsoft.com/library/#rel) części tego tematu. Te F#-określonych typów obsługuje style programowania, które są wspólne dla języków programowania funkcjonalnego. Skojarzono wiele z tych typów w modułach F# biblioteki, która obsługuje typowe operacje na tych typach.

Typ funkcji zawiera informacje na temat typów parametrów i zwracany typ.

.NET Framework jest źródłem typy obiektów, typy interfejsów, typy delegatów i inne. Można zdefiniować własne typy obiektów, podobnie jak w dowolnym języku .NET.

Ponadto F# kodu można zdefiniować aliasy, które noszą nazwy *skróty typów*, które są alternatywne nazwy dla typów. Skróty typów można użyć, gdy typ mogą ulec zmianie w przyszłości i chcesz uniknąć zmieniania kodu, który zależy od typu. Lub można użyć jako przyjazna nazwa dla typu, który może uczynić kod łatwiejsze do odczytania i zinterpretowania skrótem typu.

F#dostarcza typy przydatne kolekcji, które mają programowania funkcjonalnego, należy pamiętać. Używanie tych typów kolekcji ułatwia pisanie kodu, który jest bardziej funkcjonalnego w stylu. Aby uzyskać więcej informacji, zobacz [ F# typy kolekcji](fsharp-collection-types.md).

## <a name="syntax-for-types"></a>Składnia dla typów
W F# kodu, często musisz zapisać nazwy typów. Każdy typ ma formę składni i użycia tych formularzy składni w adnotacji typu, deklaracje metody abstrakcyjnej, deklaracje delegatów, sygnatur i innych konstrukcji. Zawsze, gdy należy zadeklarować nową konstrukcję program w interpreter, interpreter Wyświetla nazwę konstrukcja i składnię dla tego typu. Ta składnia może być tylko identyfikator typu zdefiniowanego przez użytkownika lub wbudowane identyfikatora takiego jak w przypadku `int` lub `string`, ale w przypadku bardziej złożonych typów jest bardziej złożona składnia.

W poniższej tabeli przedstawiono aspektów Składnia typu F# typów.

|Typ|Składnia typu|Przykłady|
|----|-----------|--------|
|typ pierwotny|*Nazwa typu*|`int`<br /><br />`float`<br /><br />`string`|
|odpowiedni typ agregacji (klasy, struktury, Unii, rekord, wyliczenia i tak dalej)|*Nazwa typu*|`System.DateTime`<br /><br />`Color`|
|— Skrót typu|*type-abbreviation-name*|`bigint`|
|w pełni kwalifikowanego typu|*Nazwa Namespaces.Type*<br /><br />lub<br /><br />*Nazwa Modules.Type*<br /><br />lub<br /><br />*Nazwa Namespaces.Modules.Type*|`System.IO.StreamWriter`|
|tablica|*Nazwa typu*[] lub<br /><br />*Nazwa typu* tablicy|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|dwuwymiarową tablicę|*Nazwa typu*[,]|`int[,]`<br /><br />`float[,]`|
|tablicy trójwymiarowej|*Nazwa typu*[,]|`float[,,]`|
|Krotki|*Typ Nazwa1* &#42; *Nazwa2 typu* ...|Na przykład `(1,'b',3)` ma typ `int * char * int`|
|Typ ogólny|*Parametr typu* *Nazwa typu ogólnego*<br /><br />lub<br /><br />*generic-type-name*&lt;*type-parameter-list*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|skonstruowany typ (typ ogólny, który został podany argument określonego typu)|*argument typu* *Nazwa typu ogólnego*<br /><br />lub<br /><br />*generic-type-name*&lt;*type-argument-list*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|Typ funkcji, która ma jeden parametr|*Parametr type1*  - &gt; *zwracanego typu*|Funkcja, która przyjmuje `int` i zwraca `string` ma typ `int -> string`|
|Typ funkcji, która ma wiele parametrów|*Parametr type1*  - &gt; *type2 parametr*  - &gt; ... —&gt; *zwracanego typu*|Funkcja, która przyjmuje `int` i `float` i zwraca `string` ma typ `int -> float -> string`|
|wyższe funkcji order jako parametr|(*typu funkcji*)|`List.map` ma typ `('a -> 'b) -> 'a list -> 'b list`|
|delegate|Delegowanie z *typu funkcji*|`delegate of unit -> int`|
|elastycznym typem|#*Nazwa typu*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Tematy pokrewne

|Temat|Opis|
|-----|-----------|
|[Typy pierwotne](primitive-types.md)|W tym artykule opisano wbudowanych typów prostych, takie jak typy całkowite, typ Boolean i typy znaków.|
|[Typ jednostki](unit-type.md)|W tym artykule opisano `unit` typ, typ, który posiada jedną wartość i który jest wskazywany przez (); równoważna `void` w C# i `Nothing` w języku Visual Basic.|
|[Krotki](tuples.md)|W tym artykule opisano, typu spoiny, typ, który składa się z skojarzone wartości dowolnego typu pogrupowane w pary, trójek, quadruples i tak dalej.|
|[Opcje](options.md)|Opisuje typ opcji typu, który może mieć wartość lub być pusta.|
|[Listy](lists.md)|W tym artykule opisano list, które są uporządkowane, niezmienne serię elementów wszystkie tego samego typu.|
|[Tablice](arrays.md)|W tym artykule opisano, tablice, które są uporządkowane zestawy modyfikowalnych elementów tego samego typu, które zajmują ciągłego bloku pamięci i mają stały rozmiar.|
|[Sekwencje](sequences.md)|Opisuje typ sekwencji, który reprezentuje logicznej serii wartości. poszczególne wartości są obliczane tylko w razie potrzeby.|
|[Rekordy](records.md)|Opisuje typ rekordu małych agregacji nazwanych wartości.|
|[Sumy rozłączne](discriminated-unions.md)|W tym artykule opisano dyskryminowanego typu złożenia typów, których wartości może być dowolny zestaw możliwych typów.|
|[Funkcje](functions/index.md)|W tym artykule opisano wartości funkcji.|
|[Klasy](classes.md)|W tym artykule opisano typu klasy, typ obiektu odpowiadający typowi dokumentacja platformy .NET. Typy klasy mogą zawierać elementy członkowskie, właściwości, implementowane interfejsy i typ podstawowy.|
|[Struktury](structures.md)|W tym artykule opisano `struct` typ, typ obiektu, który odnosi się do typu wartości platformy .NET. `struct` Typ zazwyczaj reprezentuje małych agregację danych.|
|[Interfejsy](interfaces.md)|Zawiera opis typów interfejsu, które są typy, które reprezentują zestaw elementów członkowskich dostarczające niektórych funkcji, ale które nie zawierają żadnych danych. Typ interfejsu muszą być zaimplementowane przez typ obiektu były przydatne.|
|[Delegaty](delegates.md)|Opisuje typ delegata, który reprezentuje funkcję jako obiekt.|
|[Wyliczenia](enumerations.md)|W tym artykule opisano typy wyliczeniowe, w których wartości należą do zestawu nazwanych wartości.|
|[Atrybuty](attributes.md)|W tym artykule opisano atrybuty, które są używane do określania metadanych dla innego typu.|
|[Typy wyjątków](exception-handling/exception-types.md)|Opisuje wyjątki, które określają informacje o błędzie.|

---
title: Typy F#
description: 'Informacje o typach, które są używane w F # oraz jak o nazwie i opisem typów F #.'
ms.date: 05/16/2016
ms.openlocfilehash: bdbb89dc751970ac31fe102df009f0bff6388e52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565592"
---
# <a name="f-types"></a>Typy F#

W tym temacie opisano typy, które są używane w F # oraz jak o nazwie i opisem typów F #.


## <a name="summary-of-f-types"></a>Podsumowanie typów F #
Niektóre typy są traktowane jako *typów pierwotnych*, takie jak typ Boolean `bool` i typów całkowitych i zmiennoprzecinkowych w punkcie o różnych rozmiarach, które obejmują typy bajtów i znaki. Te typy są opisane w [typów pierwotnych](primitive-types.md).

Inne typy, które są wbudowane w języku obejmują krotek, list, tablic, sekwencji, rekordów i Suma rozłączna Unii. Jeśli masz doświadczenie z innymi językami .NET i są uczenia F #, należy przeczytać tematy dla każdego z tych typów. Łącza do dodatkowych informacji o tych typach znajdują się w [Tematy pokrewne](https://msdn.microsoft.com/library/#rel) tego tematu. Te F #-określonych typów obsługuje style programowania, które są wspólne dla funkcjonalności języków programowania. Wiele z tych typów skojarzony modułów w bibliotece języka F # obsługujące typowe operacje na tych typów.

Typ funkcji zawiera informacje na temat typów parametrów i typ zwracany.

.NET Framework jest źródłem typów obiektów, typów interfejsów typów delegowanych i inne. Można zdefiniować własnych typów obiektów, tak samo, jak można w dowolnym języku .NET.

Ponadto w kodzie języka F # można zdefiniować aliasy, które są nazywane *skróty typów*, które są alternatywne nazwy dla typów. Skróty typów można użyć w przypadku tego typu mogą ulec zmianie w przyszłości uniknąć zmieniania kodu, która zależy od typu. Lub skrót typu można użyć jako przyjazna nazwa dla typu, który może ułatwić kodu przeczytane i zrozumiane.

F # zawiera typy przydatne kolekcji, które są przystosowane do programowania funkcyjnego w uwadze. Używanie tych typów kolekcji ułatwia pisanie kodu, który jest bardziej funkcjonalny w stylu. Aby uzyskać więcej informacji, zobacz [typy kolekcji F #](fsharp-collection-types.md).


## <a name="syntax-for-types"></a>Składnia dla typów
W kodzie języka F # często trzeba zapisać nazwy typów. Każdy typ ma formę składni i użycia tych formularzy składni w adnotacji typu, deklaracje metody abstrakcyjnej deklaracji obiektu delegowanego, sygnatur i innych konstrukcji. Zawsze, gdy deklarowaniu konstrukcję nowego programu w interpretera interpretera Wyświetla nazwę konstrukcja i składnia dla jego typu. Ta składnia może być tylko identyfikator typu zdefiniowanego przez użytkownika lub wbudowanych identyfikatora takie jak w przypadku `int` lub `string`, ale w przypadku bardziej złożonych typów składnia jest bardziej złożony.

W poniższej tabeli przedstawiono aspektów Składnia typu typów F #.



|Typ|Składnia typu|Przykłady|
|----|-----------|--------|
|Typ pierwotny|*Nazwa typu*|`int`<br /><br />`float`<br /><br />`string`|
|Typ agregacji (klasy, struktury, Unii, rekordu, wyliczenia i tak dalej)|*Nazwa typu*|`System.DateTime`<br /><br />`Color`|
|Skrót typu|*Nazwa — skrót typu*|`bigint`|
|pełny typ|*Nazwa Namespaces.Type*<br /><br />lub<br /><br />*Nazwa Modules.Type*<br /><br />lub<br /><br />*Nazwa Namespaces.Modules.Type*|`System.IO.StreamWriter`|
|tablica|*Nazwa typu*[] lub<br /><br />*Nazwa typu* tablicy|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|tablicą dwuwymiarową|*Nazwa typu*[,]|`int[,]`<br /><br />`float[,]`|
|tablicą trójwymiarową|*Nazwa typu*[,]|`float[,,]`|
|krotki|*Typ Nazwa1* &#42; *Nazwa2 typu* ...|Na przykład `(1,'b',3)` ma typ `int * char * int`|
|Typ ogólny|*Parametr typu* *nazwy typu ogólnego*<br /><br />lub<br /><br />*Nazwa typu ogólnego*&lt;*listy parametrów typu*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|tworzony typ (ogólny typ zawierający podany argument określonego typu)|*argument typu* *nazwy typu ogólnego*<br /><br />lub<br /><br />*Nazwa typu ogólnego*&lt;*listy argumentów typu*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|Typ funkcji, która ma jeden parametr|*Parametr type1*  - &gt; *zwracanego typu*|Funkcja, która przyjmuje `int` i zwraca `string` ma typ `int -> string`|
|Typ funkcji, który ma wiele parametrów|*Parametr type1*  - &gt; *type2 parametru*  - &gt; ... -&gt; *zwracanego typu*|Funkcja, która przyjmuje `int` i `float` i zwraca `string` ma typ `int -> float -> string`|
|wyższy funkcji order jako parametr|(*typu funkcji*)|`List.map` zawiera typ `('a -> 'b) -> 'a list -> 'b list`|
|delegate|Delegowanie z *typu funkcji*|`delegate of unit -> int`|
|elastyczne typu|#*Nazwa typu*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Tematy pokrewne


|Temat|Opis|
|-----|-----------|
|[Typy pierwotne](primitive-types.md)|Opisuje wbudowanych typów prostych, takie jak typy całkowite, typ Boolean i typy znaków.|
|[Typ jednostki](unit-type.md)|W tym artykule opisano `unit` typu, typu jedną wartością i która jest wskazywana przez (); równoważna `void` w języku C# i `Nothing` w języku Visual Basic.|
|[Krotki](tuples.md)|Opisuje typ krotki typu, który składa się z powiązanymi wartościami typu są pogrupowane w pary, triples quadruples i tak dalej.|
|[Opcje](options.md)|W tym artykule opisano typu opcji typu, które mogą mieć wartość lub być pusta.|
|[Listy](lists.md)|W tym artykule opisano list, które są uporządkowane, niezmienne serii elementów wszystkie tego samego typu.|
|[Tablice](arrays.md)|W tym artykule opisano tablice, które są uporządkowane zestawy modyfikowalne elementy tego samego typu, które zajmują ciągłego bloku pamięci i mają stały rozmiar.|
|[Sekwencje](sequences.md)|Opisuje typ sekwencji, który reprezentuje szereg logiczne wartości. poszczególne wartości są obliczane tylko w razie potrzeby.|
|[Rekordy](records.md)|Opisuje typ rekordu, mała agregacji nazwanych wartości.|
|[Sumy rozłączne](discriminated-unions.md)|Opisuje rozróżniane typ Unii, typ, którego wartości mogą być dowolny zestaw możliwych typów.|
|[Funkcje](functions/index.md)|Zawiera opis funkcji wartości.|
|[Klasy](classes.md)|Opisuje typ klasy, typ obiektu odpowiadający typowi odwołanie .NET. Typy klasy mogą zawierać elementów członkowskich, właściwości zaimplementowanych interfejsów i typu podstawowego.|
|[Struktury](structures.md)|W tym artykule opisano `struct` typ, typ obiektu odpowiadający typowi wartości .NET. `struct` Typ zazwyczaj reprezentuje małych agregacji danych.|
|[Interfejsy](interfaces.md)|W tym artykule opisano typy interfejsu, do których są typy, które reprezentują zestaw elementów członkowskich, które zapewniają niektórych funkcji, ale które nie zawierają danych. Typ interfejsu musi być implementowana przez typ obiektu użyteczne.|
|[Delegaci](delegates.md)|Opisuje typ delegata, który reprezentuje funkcję jako obiekt.|
|[Wyliczenia](enumerations.md)|W tym artykule opisano typy wyliczeniowe, w której wartości należą do zestawu o nazwie wartości.|
|[Atrybuty](attributes.md)|W tym artykule opisano atrybuty, które są używane do określania metadanych dla innego typu.|
|[Typy wyjątków](exception-handling/exception-types.md)|W tym artykule opisano wyjątki, które określają informacje o błędzie.|

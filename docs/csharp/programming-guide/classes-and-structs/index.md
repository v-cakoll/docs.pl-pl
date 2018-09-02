---
title: Klasy i struktury (Przewodnik programowania w języku C#)
description: W tym artykule opisano korzystanie z klas i struktur (struktury) w języku C#.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: 801f8e64bf64ee55651521ba53915000cc326303
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419579"
---
# <a name="classes-and-structs-c-programming-guide"></a>Klasy i struktury (Przewodnik programowania w języku C#)
Klasy i struktury są dwoma podstawowymi konstrukcjami wspólnego systemu typu W.NET Framework. Każdy jest zasadniczo strukturą danych, która hermetyzuje zestaw danych i zachowania, które należą ze sobą jako jednostki logicznej. Dane i zachowania są *członków* klasy lub struktury, i obejmują one metody, właściwości i zdarzenia i tak dalej, zgodnie z opisem w dalszej części tego tematu.  
  
 Deklaracja klasy lub struktury jest podobna do planu, który służy do utworzenia wystąpienia lub obiektów w czasie wykonywania. Po zdefiniowaniu klasy lub struktury o nazwie `Person`, `Person` jest nazwą typu. Jeśli zadeklarujesz i zainicjalizujesz zmienną `p` typu `Person`, `p` jest określany jako z obiektem lub wystąpieniem `Person`. Wiele wystąpień tego samego `Person` można utworzyć typu, a każde wystąpienie może mieć różne wartości we właściwościach i polach.  
  
 Klasa jest typem referencyjnym. Po utworzeniu obiektu klasy, zmienna do której przypisany jest obiekt zawiera tylko odwołanie do pamięci. Gdy odwołanie do obiektu jest przypisane do nowej zmiennej, Nowa zmienna odwołuje się do oryginalnego obiektu. Zmiany wprowadzone za pomocą jednej zmiennej są odzwierciedlane w innych zmiennych, ponieważ oba odnoszą się do tych samych danych.  
  
 Struktura jest typem wartości. Po utworzeniu struktury, zmienna, do którego jest przypisana struktura zawiera rzeczywiste dane struktury. Struktura jest przypisywana do nowej zmiennej, są kopiowane. Nowa zmienna i pierwotna zmienna zatem zawierają dwie oddzielne kopie tych samych danych. Zmiany wprowadzone w jednym egzemplarzu nie wpływają na drugi egzemplarz.  
  
 Ogólnie rzecz biorąc klasy służą do modelowania bardziej złożonych zachowań lub dane, które jest przeznaczone do modyfikacji po utworzeniu obiektu klasy. Struktury najlepiej sprawdzają się w małych strukturach danych, które zawierają głównie dane, które nie są przeznaczone do modyfikacji po utworzeniu struktury.  
  
 Aby uzyskać więcej informacji, zobacz [klasy](../../../csharp/programming-guide/classes-and-structs/classes.md), [obiektów](../../../csharp/programming-guide/classes-and-structs/objects.md), i [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `CustomClass` w `ProgrammingGuide` przestrzeń nazw ma trzy elementy członkowskie: Konstruktor wystąpienia, właściwość o nazwie `Number`i metodę o nazwie `Multiply`. `Main` Method in Class metoda `Program` klasy tworzy wystąpienie (obiekt) `CustomClass`, oraz metody i właściwości obiektu są dostępne przy użyciu notacji z kropką.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Hermetyzacja protokołu  
 *Hermetyzacja* czasami nazywa się pierwszym filarem lub zasadą programowania zorientowanego na obiekt. Zgodnie z zasadą hermetyzacji klasa lub Struktura można określić, jak każdy z jej członków jest dostępność do kodu poza klasą lub strukturą. Aby ograniczyć możliwość wystąpienia błędów kodowania lub złośliwego oprogramowania, metody i zmienne, które nie są przeznaczone do użycia z poza klasy lub zestawu mogą być ukrywane.  
  
 Aby uzyskać więcej informacji na temat klas, zobacz [klasy](../../../csharp/programming-guide/classes-and-structs/classes.md) i [obiektów](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### <a name="members"></a>Elementy członkowskie  
 Wszystkie metody, pola, stałe, właściwości i zdarzenia musi być zadeklarowana w ramach danego typu; są to tak zwane *członków* tego typu. W języku C# nie ma żadnych zmiennych globalnych ani metod w przeciwieństwie do innych języków. Nawet punktu wejścia programu `Main` metody musi być zadeklarowana w klasie lub strukturze. Poniższa lista zawiera wszystkie różne rodzaje elementów członkowskich, które może być zadeklarowana w klasie lub strukturze.  
  
-   [Pola](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [Stałe](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
  
-   [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
  
-   [Operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [Zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a>Ułatwienia dostępu  
 Niektóre metody i właściwości mają być nazywane lub dostępne z kodu spoza klasy lub struktury, znanego jako *kod klienta*. Inne metody i właściwości mogą być tylko do użytku w samej klasie lub strukturze. Należy ograniczyć dostępność kodu, tak aby tylko kod zamierzonego klienta mógł go osiągnąć. Należy określić, jak przystępna typów i ich elementów członkowskich mają kod klienta za pomocą modyfikatorów dostępu [publicznych](../../../csharp/language-reference/keywords/public.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [ chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md) i [prywatny chroniony](../../../csharp/language-reference/keywords/private-protected.md). Wartość domyślna dostępu `private`. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).   
  
### <a name="inheritance"></a>Dziedziczenie  
 Klasy (ale nie struktury) obsługują dziedziczenia. Klasa, która pochodzi z innej klasy ( *klasy bazowej*) automatycznie zawiera wszystkich publicznych, chronionych i wewnętrznych członków klasy podstawowej, z wyjątkiem jego konstruktorów i finalizatorów. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md) i [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 Klasy mogą być deklarowane jako [abstrakcyjne](../../../csharp/language-reference/keywords/abstract.md), co oznacza, że co najmniej jeden z ich metod nie mają implementacji. Mimo że nie można bezpośrednio utworzyć wystąpienia klasy abstrakcyjnej, mogą one służyć jako klay bazowe dla innych klas, którym brakuje implementacji. Klasy mogą być także zadeklarowane jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) aby dziedziczyły innych klas z nich. Aby uzyskać więcej informacji, zobacz [abstrakcyjnych i zapieczętowanych klas i składowych klasy](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Interfejsy  
 Klasy i struktury mogą odziedziczyć wiele interfejsów. Dziedziczenie od interfejsu oznacza, że typ implementuje wszystkie metody, które są zdefiniowane w interfejsie. Więcej informacji znajdziesz w artykule [Interfejsy](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="generic-types"></a>Typy ogólne  
 Klasy i struktury można zdefiniować co najmniej jeden parametr typu. Kod klienta dostarcza typu podczas tworzenia wystąpienia typu. Na przykład <xref:System.Collections.Generic.List%601> klasy w <xref:System.Collections.Generic> przestrzeń nazw została zdefiniowana za pomocą jednego parametru typu. Kod klienta tworzy instancję `List<string>` lub `List<int>` do określenia typu, który będzie przechowywać listę. Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).  
  
### <a name="static-types"></a>Typy statyczne  
 Klasy (ale nie struktury) mogą być deklarowane jako [statyczne](../../../csharp/language-reference/keywords/static.md). Klasa statyczna może zawierać tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia za pomocą słowa kluczowego new. Jedna kopia klasy jest ładowany do pamięci podczas wczytywania programu, a jej elementy członkowskie są dostępne za pośrednictwem nazwy klasy. Zarówno klasy i struktury mogą zawierać elementy statyczne. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Zagnieżdżone typy  
 Klasa lub struktura może być zagnieżdżona w innej klasie lub strukturze. Aby uzyskać więcej informacji, zobacz [Typy zagnieżdżone](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### <a name="partial-types"></a>Typy częściowe  
 Można zdefiniować część klasy, struktury lub metody w jednym pliku kodu i drugą część w osobnym pliku kodu. Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicjatory obiektów  
 Możesz można utworzyć wystąpienia i zainicjalizować klasy lub obiektów struct i kolekcji obiektów, bez jawnego wywołania ich konstruktora. Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Typy anonimowe  
 W sytuacjach, gdy nie jest wygodne lub niezbędne do utworzenia nazwanej klasy na przykład podczas wypełniania listy przy użyciu danych struktury, nie trzeba powtarzać lub przechodzić do innej metody, należy użyć typów anonimowych. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### <a name="extension-methods"></a>Metody rozszerzeń  
 Możesz "rozszerzyć" klasy bez tworzenia klasy pochodnej poprzez utworzenie oddzielnego typu, którego metody mogą być wywoływane tak, jakby jakby należały do oryginalnego typu. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Jawnie wpisana zmienna lokalna  
 Wewnątrz metody klasy lub struktury można użyć niejawnego wpisywania w celu poinstruowania kompilatora do określenia poprawnego typu w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)

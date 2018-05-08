---
title: Klasy i struktury (Przewodnik programowania w języku C#)
description: Zawiera opis klas i struktur (struktury) w języku C#.
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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="classes-and-structs-c-programming-guide"></a>Klasy i struktury (Przewodnik programowania w języku C#)
Klasy i struktury są dwa podstawowe konstrukcje system typu wspólnego w programie .NET Framework. Każdy jest zasadniczo to struktura danych, która hermetyzuje zestaw danych i zachowania, które należy razem jako jednostki logicznej. Danych i zachowania *członków* klasy lub struktury, i wymienionych w dalszej części tego tematu zawierają metody, właściwości i zdarzeń i tak dalej.  
  
 Deklaracja klasy lub struktury jest podobny do planu, który jest używany do tworzenia wystąpień lub obiektów w czasie wykonywania. Po zdefiniowaniu klasy lub struktury o nazwie `Person`, `Person` jest nazwa typu. Jeśli zadeklarować i zainicjuj zmienną `p` typu `Person`, `p` jest określany jako obiektu lub wystąpienie `Person`. Wiele wystąpień tego samego `Person` można utworzyć typu, a każde wystąpienie mogą mieć różne wartości w polach i właściwości.  
  
 Klasa jest typem referencyjnym. Po utworzeniu obiektu klasy zmiennej, do której przypisano obiekt zawiera tylko odwołanie do pamięci. Gdy odwołanie do obiektu jest przypisany do nowej zmiennej, nowej zmiennej odwołuje się do oryginalnego obiektu. Zmiany wprowadzane za pośrednictwem jednej zmiennej są odzwierciedlane w innej zmiennej obydwie odwołuje się do tych samych danych.  
  
 Struktury jest typem wartości. Podczas tworzenia struktury zmiennej, do której przypisano struktury zawiera struktury danych rzeczywistych. Struktura jest przypisany do nowej zmiennej, są kopiowane. Nową zmienną i pierwotnej zmiennej w związku z tym zawierają dwa osobne kopie tych samych danych. Zmiany wprowadzone w jednej kopii nie wpływają na innej kopii.  
  
 Ogólnie rzecz biorąc klasy służą do modelowania bardziej złożonych zachowanie lub dane, które ma na celu można zmodyfikować po utworzeniu obiektu klasy. Struktury są najbardziej odpowiednie dla struktur danych w małych, które zawierają głównie dane, które nie jest przeznaczona do można zmodyfikować po utworzeniu struktury.  
  
 Aby uzyskać więcej informacji, zobacz [klasy](../../../csharp/programming-guide/classes-and-structs/classes.md), [obiektów](../../../csharp/programming-guide/classes-and-structs/objects.md), i [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `CustomClass` w `ProgrammingGuide` przestrzeń nazw ma trzy elementy członkowskie: konstruktor wystąpień, właściwość o nazwie `Number`i metodę o nazwie `Multiply`. `Main` Metody w `Program` klasy tworzy wystąpienie (obiekt) `CustomClass`, oraz metody i właściwości obiektu są dostępne przy użyciu notacji kropki.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Hermetyzacja protokołu  
 *Hermetyzacja* jest czasami nazywany pierwszego słupka lub zasada programowanie zorientowane obiektowo. Zgodnie z zasadą hermetyzacji klasie lub strukturze można określić, jak przystępna wszystkich członków jest kod poza klasą lub strukturą. Aby ograniczyć możliwość kodowania błędy lub złośliwe oprogramowanie może być ukryte metod i zmienne, które nie są przeznaczone do użycia w poza klasy lub zestawu.  
  
 Aby uzyskać więcej informacji na temat klas, zobacz [klasy](../../../csharp/programming-guide/classes-and-structs/classes.md) i [obiektów](../../../csharp/programming-guide/classes-and-structs/objects.md).  
  
### <a name="members"></a>Elementy członkowskie  
 Wszystkie metody, pola, stałe, właściwości i zdarzenia musi być zadeklarowana w typie; są one nazywane *członków* typu. W języku C# nie ma żadnych zmiennych globalnych ani metod się w przypadku niektórych innych języków. Nawet punktu wejścia programu `Main` metody, musi być zadeklarowana w klasie lub strukturze. Poniższa lista zawiera opisano różne typy elementów członkowskich, które może być zadeklarowana w klasie lub strukturze.  
  
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
 Niektóre metody i właściwości, które są przeznaczone do można wywołać lub uzyskać dostępu do z kodu spoza Twojej klasy lub struktury, znany jako *kodu klienta*. Inne metody i właściwości mogą być tylko do użytku w klasie lub strukturze, samej siebie. Należy ograniczyć ułatwień dostępu kodu, tak aby tylko kodu przeznaczone klienckich można uzyskać do niej dostęp. Można zdecydować, jak przystępna z typów i ich elementy członkowskie do kodu klienta za pomocą modyfikatorów dostępu [publicznego](../../../csharp/language-reference/keywords/public.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [ chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md) i [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md). Dostępność domyślny jest `private`. Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### <a name="inheritance"></a>Dziedziczenie  
 Klasy (ale nie struktury) obsługuje koncepcja dziedziczenia. Klasa, która pochodzi z innej klasy ( *klasa podstawowa*) automatycznie zawiera wszystkich publicznych, chronionych i wewnętrznych elementów członkowskich klasy podstawowej, z wyjątkiem jej konstruktorów i finalizatory. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md) i [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
 Klasy może być zadeklarowana jako [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md), co oznacza, że przynajmniej jedna z metod nie ma żadnej implementacji. Mimo że nie można bezpośrednio utworzyć wystąpienia klasy abstrakcyjnej, mogą stanowić klasy podstawowe dla innych klas, które zapewniają Brak implementacji. Klasy mogą również być deklarowane jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) aby dziedziczyły innych klas z nich. Aby uzyskać więcej informacji, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Interfejsy  
 Klasy i struktury może dziedziczyć wiele interfejsów. Można dziedziczyć interfejsu oznacza, że typ implementuje wszystkie metody, które są zdefiniowane w interfejsie. Aby uzyskać więcej informacji, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="generic-types"></a>Typy ogólne  
 Można zdefiniować klasy i struktury z co najmniej jednego parametru typu. Kod klienta zawiera typ, podczas tworzenia wystąpienia typu. Na przykład <xref:System.Collections.Generic.List%601> klasy w <xref:System.Collections.Generic> przestrzeni nazw jest zdefiniowana z parametrem typu. Kod klienta tworzy wystąpienie `List<string>` lub `List<int>` do określania typu, w którym będą przechowywane listy. Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).  
  
### <a name="static-types"></a>Statyczne typy  
 Klasy (ale nie struktury) mogą być deklarowane jako [statycznych](../../../csharp/language-reference/keywords/static.md). Klasa statyczna może zawierać tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia o słowo kluczowe new. Jedna kopia klasy jest ładowany do pamięci podczas ładowania programu i jej elementów członkowskich są dostępne za pośrednictwem nazwy klasy. Zarówno klas i struktur może zawierać statycznych elementów członkowskich. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Zagnieżdżone typy  
 Klasy lub struktury, może być zagnieżdżona w innej klasy lub struktury. Aby uzyskać więcej informacji, zobacz [zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md).  
  
### <a name="partial-types"></a>Typy częściowe  
 Można zdefiniować klasy, struktury lub metoda w jednym pliku kodu i inną część w osobnym pliku kodu. Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicjatory obiektów  
 Można utworzyć wystąpienia i zainicjować klasy lub struktury obiektów i kolekcji obiektów, bez jawnie podczas wywoływania konstruktora ich. Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Typy anonimowe  
 W sytuacjach, gdy nie jest wygodne lub niezbędne do utworzenia nazwanego klasy na przykład gdy są podczas wypełniania listy z danymi konstrukcje że nie trzeba zachować lub Przekaż do innej metody, można użyć typów anonimowych. Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
### <a name="extension-methods"></a>Metody rozszerzeń  
 Można "rozszerzyć" klasy bez tworzenia klasy pochodnej przez utworzenie oddzielnych typu, której metody można wywołać tak, jakby należały do oryginalnego typu. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Jawnie wpisana zmienna lokalna  
 W klasie lub strukturze — metoda umożliwia wpisywanie niejawne poinstruować kompilator, aby ustalić poprawnego typu w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)

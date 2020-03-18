---
title: Klasy i struktury - Przewodnik programowania C#
description: Opisuje użycie klas i struktur (struktur) w języku C#.
ms.date: 01/17/2016
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
ms.openlocfilehash: afd9e688bd716375bafb370fad4af082a9498411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399855"
---
# <a name="classes-and-structs-c-programming-guide"></a>Klasy i struktury (Przewodnik programowania w języku C#)
Klasy i struktury są dwie podstawowe konstrukcje systemu wspólnego typu w .NET Framework. Każdy z nich jest zasadniczo struktury danych, która hermetyzuje zestaw danych i zachowań, które należą do siebie jako jednostka logiczna. Dane i zachowania są *członkami* klasy lub struktury i zawierają jego metody, właściwości i zdarzenia itd., jak wymieniono w dalszej części tego tematu.  
  
 Klasa lub struktura deklaracji jest jak plan, który jest używany do tworzenia wystąpień lub obiektów w czasie wykonywania. Jeśli zdefiniujesz klasę `Person`lub `Person` strukturę o nazwie , jest nazwą typu. Jeśli deklarujesz i inicjujesz `p` zmienną typu `Person`, `p` jest `Person`uważana za obiekt lub wystąpienie . Można utworzyć wiele `Person` wystąpień tego samego typu, a każde wystąpienie może mieć różne wartości we właściwościach i polach.  
  
 Klasa jest typem odwołania. Po utworzeniu obiektu klasy zmienna, do której jest przypisany obiekt, przechowuje tylko odwołanie do tej pamięci. Gdy odwołanie do obiektu jest przypisane do nowej zmiennej, nowa zmienna odwołuje się do oryginalnego obiektu. Zmiany wprowadzone za pośrednictwem jednej zmiennej są odzwierciedlane w drugiej zmiennej, ponieważ oba odnoszą się do tych samych danych.  
  
 Struktura jest typem wartości. Po utworzeniu struktury zmienna, do której jest przypisany strukturę, przechowuje rzeczywiste dane struct. Gdy struktura jest przypisana do nowej zmiennej, jest kopiowana. Nowa zmienna i oryginalna zmienna zawierają zatem dwie oddzielne kopie tych samych danych. Zmiany wprowadzone w jednej kopii nie mają wpływu na drugą kopię.  
  
 Ogólnie rzecz biorąc klasy są używane do modelowania bardziej złożone zachowanie lub dane, które ma być modyfikowane po utworzeniu obiektu klasy. Struktury najlepiej nadają się do małych struktur danych, które zawierają przede wszystkim dane, które nie są przeznaczone do modyfikowania po utworzeniu struktury.  
  
 Aby uzyskać więcej informacji, zobacz [Klasy](./classes.md), [Obiekty](./objects.md)i [Typy struktury](../../language-reference/builtin-types/struct.md).  
  
## <a name="example"></a>Przykład  
 W poniższym `CustomClass` przykładzie `ProgrammingGuide` w obszarze nazw ma trzy elementy członkowskie: `Number`konstruktor `Multiply`wystąpienia, właściwość o nazwie i metodę o nazwie . Metoda `Main` w `Program` klasie tworzy wystąpienie (obiekt) `CustomClass`, a metoda obiektu i właściwość są dostępne przy użyciu notacji kropki.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Hermetyzacja  
 *Hermetyzacja* jest czasami określana jako pierwszy filar lub zasada programowania obiektowego. Zgodnie z zasadą hermetyzacji, klasy lub struktury można określić, jak dostępne każdego z jego członków jest kod poza klasą lub struktury. Metody i zmienne, które nie są przeznaczone do użycia spoza klasy lub zestawu mogą być ukryte, aby ograniczyć możliwość kodowania błędów lub złośliwych exploitów.  
  
 Aby uzyskać więcej informacji na temat klas, zobacz [Klasy](./classes.md) i [obiekty](./objects.md).  
  
### <a name="members"></a>Elementy członkowskie  
 Wszystkie metody, pola, stałe, właściwości i zdarzenia muszą być zadeklarowane w obrębie typu; są one nazywane *członkami* typu. W języku C#, nie ma żadnych zmiennych globalnych lub metod, ponieważ istnieją w niektórych innych językach. Nawet punkt wejścia programu, `Main` metoda, musi być zadeklarowana w klasie lub strukturze. Poniższa lista zawiera wszystkie różne rodzaje elementów członkowskich, które mogą być zadeklarowane w klasie lub strukturze.  
  
- [Pola](./fields.md)  
  
- [Stałe](./constants.md)  
  
- [Właściwości](./properties.md)  
  
- [Metody](./methods.md)  
  
- [Konstruktory](./constructors.md)  
  
- [Zdarzenia](../events/index.md)  
  
- [Finalizatory](./destructors.md)  
  
- [Indexers](../indexers/index.md) (Indeksatory)  
  
- [Operatory](../../language-reference/operators/index.md)  
  
- [Zagnieżdżone typy](./nested-types.md)  
  
### <a name="accessibility"></a>Ułatwienia dostępu  
 Niektóre metody i właściwości są przeznaczone do wywoływania lub uzyskiwania do nich dostępu z kodu poza klasą lub strukturą, znaną jako *kod klienta.* Inne metody i właściwości mogą być tylko do użytku w klasie lub struktury się. Ważne jest, aby ograniczyć dostępność kodu, tak aby można było go osiągnąć tylko kod klienta. Można określić, jak dostępne są twoje typy i ich elementy członkowskie do kodu klienta za pomocą modyfikatorów dostępu [publicznych,](../../language-reference/keywords/public.md) [chronionych,](../../language-reference/keywords/protected.md) [wewnętrznych,](../../language-reference/keywords/internal.md) [chronionych wewnętrznych,](../../language-reference/keywords/protected-internal.md) [prywatnych](../../language-reference/keywords/private.md) i [prywatnych chronionych.](../../language-reference/keywords/private-protected.md) Domyślną ustawą o dostępności jest `private`. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
### <a name="inheritance"></a>Dziedziczenie  
 Klasy (ale nie struktury) obsługują pojęcie dziedziczenia. Klasa, która pochodzi z innej klasy *(klasa podstawowa*) automatycznie zawiera wszystkie publiczne, chronione i wewnętrzne elementy członkowskie klasy podstawowej, z wyjątkiem jego konstruktorów i finalizatorów. Aby uzyskać więcej informacji, zobacz [Dziedziczenie](./inheritance.md) i [Polimorfizm](./polymorphism.md).  
  
 Klasy mogą być zadeklarowane jako [abstrakcyjne](../../language-reference/keywords/abstract.md), co oznacza, że co najmniej jedna z ich metod nie ma implementacji. Mimo że klasy abstrakcyjne nie mogą być tworzone bezpośrednio, mogą służyć jako klasy podstawowe dla innych klas, które zapewniają brakujących implementacji. Klasy mogą być również zadeklarowane jako [zapieczętowane,](../../language-reference/keywords/sealed.md) aby uniemożliwić innym klasom dziedziczenie z nich. Aby uzyskać więcej informacji, zobacz [Klasy abstrakcyjne i zapieczętowane oraz Członkowie klasy](./abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Interfejsy  
 Klasy i struktury mogą dziedziczyć wiele interfejsów. Dziedziczenie z interfejsu oznacza, że typ implementuje wszystkie metody zdefiniowane w interfejsie. Aby uzyskać więcej informacji, zobacz [Interfejsy](../interfaces/index.md).  
  
### <a name="generic-types"></a>Typy ogólne  
 Klasy i struktury można zdefiniować za pomocą jednego lub więcej parametrów typu. Kod klienta dostarcza tego typu, gdy tworzy wystąpienie typu. Na przykład <xref:System.Collections.Generic.List%601> Klasa <xref:System.Collections.Generic> w obszarze nazw jest zdefiniowana z jednym parametrem typu. Kod klienta tworzy wystąpienie `List<string>` `List<int>` lub określić typ, który będzie przechowywać na liście. Aby uzyskać więcej informacji, zobacz [Generyk .](../generics/index.md)  
  
### <a name="static-types"></a>Typy statyczne  
 Klasy (ale nie struktury) można zadeklarować jako [statyczne](../../language-reference/keywords/static.md). Klasa statyczna może zawierać tylko statyczne elementy członkowskie i nie może być tworzone z nowym słowem kluczowym. Jedna kopia klasy jest ładowany do pamięci, gdy program ładuje, a jego elementy członkowskie są dostępne za pośrednictwem nazwy klasy. Zarówno klasy, jak i struktury mogą zawierać elementy członkowskie statyczne. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](./static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Zagnieżdżone typy  
 Klasa lub struktura mogą być zagnieżdżone w innej klasie lub strukturze. Aby uzyskać więcej informacji, zobacz [Typy zagnieżdżone](./nested-types.md).  
  
### <a name="partial-types"></a>Typy częściowe  
 Część klasy, struktury lub metody można zdefiniować w jednym pliku kodu i innej części w oddzielnym pliku kodu. Aby uzyskać więcej informacji, zobacz [Klasy częściowe i metody](./partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicjatory obiektów  
 Można utworzyć wystąpienia i zainicjować klasy lub struktury obiektów i kolekcji obiektów, bez jawnie wywoływania ich konstruktora. Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Typy anonimowe  
 W sytuacjach, gdy nie jest wygodne lub konieczne do utworzenia nazwanej klasy, na przykład podczas wypełniania listy ze strukturami danych, które nie trzeba utrwalić lub przekazać do innej metody, należy użyć typów anonimowych. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](./anonymous-types.md).  
  
### <a name="extension-methods"></a>Metody rozszerzeń  
 Klasę można "rozszerzyć" bez tworzenia klasy pochodnej, tworząc oddzielny typ, którego metody można wywołać tak, jakby należały do oryginalnego typu. Aby uzyskać więcej informacji, zobacz [Metody rozszerzenia](./extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Jawnie wpisana zmienna lokalna  
 W ramach klasy lub metody struktury, można użyć niejawnego pisania, aby poinstruować kompilator, aby określić poprawny typ w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](./implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)

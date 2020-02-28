---
title: Klasy i struktury — C# Przewodnik programowania
description: Opisuje użycie klas i struktur (struktur) w programie C#.
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
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673423"
---
# <a name="classes-and-structs-c-programming-guide"></a>Klasy i struktury (Przewodnik programowania w języku C#)
Klasy i struktury są dwoma podstawowymi konstrukcjami systemu wspólnego typu w .NET Framework. Każda z nich jest zasadniczo strukturą danych, która hermetyzuje zestaw danych i zachowań, które należą do jednostki logicznej. Dane i zachowania są *elementami członkowskimi* klasy lub struktury, a także zawierają metody, właściwości i zdarzenia itd., jak opisano w dalszej części tego tematu.  
  
 Deklaracja klasy lub struktury jest taka sama jak plan, który jest używany do tworzenia wystąpień lub obiektów w czasie wykonywania. Jeśli zdefiniujesz klasę lub strukturę o nazwie `Person`, `Person` jest nazwą typu. Jeśli zadeklarujesz i zainicjujesz zmienną `p` typu `Person`, `p` jest określana jako obiekt lub wystąpienie `Person`. Można utworzyć wiele wystąpień tego samego typu `Person`, a każde wystąpienie może mieć różne wartości w jego właściwościach i polach.  
  
 Klasa jest typem referencyjnym. Po utworzeniu obiektu klasy zmienna, do której przypisany jest obiekt, zawiera tylko odwołanie do tej pamięci. Gdy odwołanie do obiektu jest przypisane do nowej zmiennej, Nowa zmienna odwołuje się do oryginalnego obiektu. Zmiany wprowadzone za pomocą jednej zmiennej są odzwierciedlane w innej zmiennej, ponieważ odwołują się do tych samych danych.  
  
 Struktura jest typem wartości. Po utworzeniu struktury zmienna, do której jest przypisana struktura, zawiera rzeczywiste dane struktury. Gdy struktura jest przypisana do nowej zmiennej, zostanie ona skopiowana. Nowa zmienna i oryginalna zmienna w związku z tym zawierają dwie oddzielne kopie tych samych danych. Zmiany wprowadzone w jednej kopii nie mają wpływu na inną kopię.  
  
 Ogólnie rzecz biorąc, klasy są używane do modelowania bardziej złożonej zachowań lub dane, które mają być modyfikowane po utworzeniu obiektu klasy. Struktury są najlepiej dostosowane do małych struktur danych, które zawierają głównie dane, które nie są przeznaczone do modyfikacji po utworzeniu struktury.  
  
 Aby uzyskać więcej informacji, zobacz [klasy](./classes.md), [obiekty](./objects.md)i [typy struktur](../../language-reference/builtin-types/struct.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `CustomClass` w przestrzeni nazw `ProgrammingGuide` ma trzy składowe: Konstruktor wystąpienia, właściwość o nazwie `Number`i metodę o nazwie `Multiply`. Metoda `Main` w klasie `Program` tworzy wystąpienie (obiekt) `CustomClass`, a metoda i właściwość obiektu są dostępne przy użyciu notacji kropkowej.
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a>Encapsulation  
 *Hermetyzacja* jest czasami określana jako pierwszy filar lub zasada programowania zorientowanego obiektowo. Zgodnie z zasadą hermetyzacji, Klasa lub struktura może określać, jak dostępne są poszczególne elementy członkowskie w kodzie poza klasą lub strukturą. Metody i zmienne, które nie są przeznaczone do użycia poza klasą lub zestawem, mogą być ukryte, aby ograniczyć liczbę błędów lub złośliwych luk w zabezpieczeniach.  
  
 Aby uzyskać więcej informacji na temat klas, zobacz [klasy](./classes.md) i [obiekty](./objects.md).  
  
### <a name="members"></a>Elementy członkowskie  
 Wszystkie metody, pola, stałe, właściwości i zdarzenia muszą być zadeklarowane w obrębie typu; są one nazywane *elementami członkowskimi* typu. W C#programie nie istnieją zmienne globalne ani metody, które są w innych językach. Nawet punktu wejścia programu, Metoda `Main` musi być zadeklarowana w obrębie klasy lub struktury. Poniższa lista zawiera wszystkie różne rodzaje elementów członkowskich, które mogą być zadeklarowane w klasie lub strukturze.  
  
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
 Niektóre metody i właściwości mają być wywoływane lub dostępne z kodu poza klasą lub strukturą, znaną jako *kod klienta*. Inne metody i właściwości mogą być używane tylko w samej klasie lub strukturze. Ważne jest, aby ograniczyć dostępność kodu, tak aby można było uzyskać do niego tylko kod zamierzonego klienta. Możesz określić, jak dostępne typy i ich elementy członkowskie mają być kodem klienta przy użyciu modyfikatorów dostępu [Public](../../language-reference/keywords/public.md), [Protected](../../language-reference/keywords/protected.md), [Internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [Private](../../language-reference/keywords/private.md) i [Private](../../language-reference/keywords/private-protected.md). Domyślna dostępność jest `private`. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](./access-modifiers.md).  
  
### <a name="inheritance"></a>Dziedziczenie  
 Klasy (ale nie struktury) obsługują koncepcję dziedziczenia. Klasa, która dziedziczy z innej klasy ( *Klasa bazowa*), automatycznie zawiera wszystkie publiczne, chronione i wewnętrzne elementy członkowskie klasy podstawowej, z wyjątkiem konstruktorów i finalizatorów. Aby uzyskać więcej informacji, zobacz [dziedziczenie](./inheritance.md) i [polimorfizm](./polymorphism.md).  
  
 Klasy mogą być deklarowane jako [abstrakcyjne](../../language-reference/keywords/abstract.md), co oznacza, że co najmniej jedna z tych metod nie ma implementacji. Chociaż klasy abstrakcyjne nie mogą być tworzone bezpośrednio, mogą służyć jako klasy bazowe dla innych klas, które zapewniają brakującą implementację. Klasy mogą być również zadeklarowane jako [zapieczętowane](../../language-reference/keywords/sealed.md) , aby uniemożliwić innym klasom dziedziczenie z nich. Aby uzyskać więcej informacji, zobacz [klasy abstrakcyjne i zapieczętowane oraz składowe klas](./abstract-and-sealed-classes-and-class-members.md).  
  
### <a name="interfaces"></a>Interfejsy  
 Klasy i struktury mogą dziedziczyć wiele interfejsów. Aby dziedziczyć z interfejsu, oznacza, że typ implementuje wszystkie metody zdefiniowane w interfejsie. Aby uzyskać więcej informacji, zobacz [interfejsy](../interfaces/index.md).  
  
### <a name="generic-types"></a>Typy ogólne  
 Klasy i struktury można definiować przy użyciu co najmniej jednego parametru typu. Kod klienta dostarcza typ podczas tworzenia wystąpienia typu. Na przykład Klasa <xref:System.Collections.Generic.List%601> w przestrzeni nazw <xref:System.Collections.Generic> jest zdefiniowana z jednym parametrem typu. Kod klienta tworzy wystąpienie `List<string>` lub `List<int>`, aby określić typ, który będzie przechowywany na liście. Aby uzyskać więcej informacji, zobacz [Ogólne](../generics/index.md).  
  
### <a name="static-types"></a>Typy statyczne  
 Klasy (ale nie struktury) mogą być deklarowane jako [statyczne](../../language-reference/keywords/static.md). Klasa statyczna może zawierać tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia z nowym słowem kluczowym. Jedna kopia klasy jest ładowana do pamięci podczas ładowania programu, a jej elementy członkowskie są dostępne za pomocą nazwy klasy. Obie klasy i struktury mogą zawierać statyczne składowe. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klas](./static-classes-and-static-class-members.md).  
  
### <a name="nested-types"></a>Zagnieżdżone typy  
 Klasa lub struktura może być zagnieżdżona w innej klasie lub strukturze. Aby uzyskać więcej informacji, zobacz [typy zagnieżdżone](./nested-types.md).  
  
### <a name="partial-types"></a>Typy częściowe  
 Można zdefiniować część klasy, struktury lub metody w jednym pliku kodu i innej części w osobnym pliku kodu. Aby uzyskać więcej informacji, zobacz [częściowe klasy i metody](./partial-classes-and-methods.md).  
  
### <a name="object-initializers"></a>Inicjatory obiektów  
 Można tworzyć wystąpienia i inicjować obiekty klasy lub struktury oraz kolekcje obiektów, bez jawnego wywołania konstruktora. Aby uzyskać więcej informacji, zobacz [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md).  
  
### <a name="anonymous-types"></a>Typy anonimowe  
 W sytuacjach, gdy nie jest to wygodne ani konieczne do utworzenia nazwanej klasy, na przykład podczas wypełniania listy strukturami danych, które nie muszą być utrwalane lub przekazywane do innej metody, używasz typów anonimowych. Aby uzyskać więcej informacji, zobacz [Typy anonimowe](./anonymous-types.md).  
  
### <a name="extension-methods"></a>Metody rozszerzenia  
 Można "zwiększyć" klasy bez tworzenia klasy pochodnej przez utworzenie oddzielnego typu, którego metody mogą być wywoływane tak, jakby należały do oryginalnego typu. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](./extension-methods.md).  
  
### <a name="implicitly-typed-local-variables"></a>Jawnie wpisana zmienna lokalna  
 W ramach metody klasy lub struktury można użyć niejawnego wpisywania, aby nakazać kompilatorowi określenie poprawnego typu w czasie kompilacji. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](./implicitly-typed-local-variables.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)

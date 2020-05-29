---
title: Typy podstawowe — Przewodnik C#
description: Informacje o typach podstawowych (liczbowych, ciągach i obiektach) we wszystkich programach C#
ms.date: 10/10/2016
ms.technology: csharp-fundamentals
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 468482bd1b4f1a5835df9d66ee483edc33c28f61
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202210"
---
# <a name="types-variables-and-values"></a>Typy, zmienne i wartości

C# jest jednoznacznie określonym językiem. Każda zmienna i stała ma typ, tak jak każde wyrażenie, którego wynikiem jest wartość. Każdy podpis metody Określa typ dla każdego parametru wejściowego i dla zwracanej wartości. Biblioteka klas .NET Framework definiuje zestaw wbudowanych typów liczbowych, a także bardziej złożone typy, które reprezentują szeroką gamę konstrukcji logicznych, takich jak system plików, połączenia sieciowe, kolekcje i tablice obiektów oraz daty. Typowy program C# używa typów z biblioteki klas, a także typów zdefiniowanych przez użytkownika, które są modelami koncepcji specyficznych dla domeny problemu programu.  
  
Informacje przechowywane w typie mogą obejmować następujące elementy:  
  
- Miejsce do magazynowania, którego wymagana jest zmienna typu.  
  
- Wartości maksymalne i minimalne, które może reprezentować.  
  
- Elementy członkowskie (metody, pola, zdarzenia itd.), które zawiera.  
  
- Typ podstawowy, z którego dziedziczy.  
  
- Lokalizacja, w której zostanie przypisana pamięć dla zmiennych w czasie wykonywania.  
  
- Rodzaje operacji, które są dozwolone.  
  
Kompilator używa informacji o typie, aby upewnić się, że wszystkie operacje wykonywane w kodzie są *bezpieczne*. Na przykład jeśli deklarujesz zmienną typu [int](language-reference/builtin-types/integral-numeric-types.md), kompilator pozwala używać zmiennej w operacjach dodawania i odejmowania. Jeśli spróbujesz wykonać te same operacje na zmiennej typu [bool](language-reference/builtin-types/bool.md), kompilator generuje błąd, jak pokazano w następującym przykładzie:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> Deweloperzy C i C++, Zauważ, że w języku C#, [bool](language-reference/builtin-types/bool.md) nie jest konwertowany na [int](language-reference/builtin-types/integral-numeric-types.md).  
  
Kompilator osadza informacje o typie pliku wykonywalnego jako metadane. Środowisko uruchomieniowe języka wspólnego (CLR) używa tych metadanych w czasie wykonywania, aby zapewnić bezpieczeństwo typów podczas przydzielania i odzyskania pamięci.  

## <a name="specifying-types-in-variable-declarations"></a>Określanie typów w deklaracjach zmiennych

W przypadku deklarowania zmiennej lub stałej w programie należy określić jej typ lub użyć słowa kluczowego [var](language-reference/keywords/var.md) , aby zezwolić kompilatorowi na wnioskowanie typu. W poniższym przykładzie przedstawiono niektóre deklaracje zmiennych, które używają wbudowanych typów liczbowych i złożonych typów zdefiniowanych przez użytkownika:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Typy parametrów metod i zwracanych wartości są określone w podpisie metody. Następujący podpis przedstawia metodę, która wymaga [int](language-reference/builtin-types/integral-numeric-types.md) jako argumentu wejściowego i zwraca ciąg:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Po zadeklarowaniu zmiennej nie można jej ponownie zadeklarować przy użyciu nowego typu i nie można przypisać do niej wartości, która nie jest zgodna z zadeklarowanym typem. Na przykład nie można zadeklarować [int](language-reference/builtin-types/integral-numeric-types.md) , a następnie przypisać mu wartości logicznej `true` . Jednak wartości mogą być konwertowane na inne typy, na przykład wtedy, gdy są przypisane do nowych zmiennych lub przekazane jako argumenty metody. *Konwersja typu* , która nie powoduje utraty danych, jest wykonywana automatycznie przez kompilator. Konwersja, która może spowodować utratę danych, wymaga *rzutowania* w kodzie źródłowym.

Aby uzyskać więcej informacji, zobacz [rzutowanie i konwersje typów](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Typy wbudowane

Język C# zawiera standardowy zestaw wbudowanych typów liczbowych reprezentujących liczby całkowite, wartości zmiennoprzecinkowe, wyrażenia logiczne, znaki tekstowe, wartości dziesiętne i inne typy danych. Istnieją również wbudowane typy **ciągów** i **obiektów** . Są one dostępne do użycia w dowolnym programie w języku C#. Aby zapoznać się z pełną listą typów wbudowanych, zobacz [typy wbudowane](language-reference/builtin-types/built-in-types.md).
  
## <a name="custom-types"></a>Typy niestandardowe

Do tworzenia własnych typów niestandardowych służy konstrukcja [struct](language-reference/builtin-types/struct.md), [Class](language-reference/keywords/class.md), [Interface](language-reference/keywords/interface.md)i [enum](language-reference/builtin-types/enum.md) . Sama Biblioteka klas .NET Framework jest kolekcją typów niestandardowych dostarczanych przez firmę Microsoft, których można używać we własnych aplikacjach. Domyślnie najczęściej używane typy w bibliotece klas są dostępne w dowolnym programie w języku C#. Inne stają się dostępne tylko wtedy, gdy jawnie dodasz odwołanie do projektu do zestawu, w którym są zdefiniowane. Gdy kompilator ma odwołanie do zestawu, można zadeklarować zmienne (i stałe) typów zadeklarowanych w tym zestawie w kodzie źródłowym.
  
## <a name="generic-types"></a>Typy ogólne

Typ może być zadeklarowany z co najmniej jednym *parametrem typu* , który służy jako symbol zastępczy dla rzeczywistego typu ( *konkretny typ*), który będzie używany przez kod klienta podczas tworzenia wystąpienia typu. Takie typy są nazywane *typami ogólnymi*. Na przykład typ .NET Framework <xref:System.Collections.Generic.List%601> ma jeden parametr typu, który zgodnie z Konwencją otrzymuje nazwę *T*. Podczas tworzenia wystąpienia typu należy określić typ obiektów, które będzie zawierać lista, na przykład ciąg:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Użycie parametru typu umożliwia ponowne użycie tej samej klasy do przechowywania dowolnego typu elementu, bez konieczności konwertowania każdego elementu na [obiekt](language-reference/builtin-types/reference-types.md#the-object-type). Klasy kolekcji generycznej są nazywane *kolekcjami silnie określonymi* , ponieważ kompilator zna określony typ elementów kolekcji i może zgłosić błąd w czasie kompilacji, jeśli na przykład próbujesz dodać liczbę całkowitą do `strings` obiektu w poprzednim przykładzie. Aby uzyskać więcej informacji, zobacz [Ogólne](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Typy niejawne, typy anonimowe i typy krotek

Jak wspomniano wcześniej, można niejawnie wpisać zmienną lokalną (ale nie składową klasy) za pomocą słowa kluczowego [var](language-reference/keywords/var.md) . Zmienna nadal otrzymuje typ w czasie kompilacji, ale typ jest dostarczany przez kompilator. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
W niektórych przypadkach nie jest wygodne tworzenie nazwanego typu dla prostych zestawów powiązanych wartości, które nie mają być przechowywane ani przekazywane poza granicami metod. W tym celu można utworzyć *Typy anonimowe* . Aby uzyskać więcej informacji, zobacz [Typy anonimowe](programming-guide/classes-and-structs/anonymous-types.md).

Często należy zwrócić więcej niż jedną wartość z metody. Można tworzyć *typy krotek* , które zwracają wiele wartości w jednym wywołaniu metody. Aby uzyskać więcej informacji, zobacz [krotki](tuples.md).

## <a name="the-common-type-system"></a>Wspólny system typów

Ważne jest, aby zrozumieć dwa podstawowe punkty o systemie typów w .NET Framework:  
  
- Obsługuje zasady dziedziczenia. Typy mogą pochodzić od innych typów, nazywanych *typami podstawowymi*. Typ pochodny dziedziczy (z pewnymi ograniczeniami) metody, właściwości i inne elementy członkowskie typu podstawowego. Typ podstawowy może być pochodny od innego typu, w tym przypadku typ pochodny dziedziczy elementy członkowskie obu typów podstawowych w hierarchii dziedziczenia. Wszystkie typy, w tym wbudowane typy liczbowe, takie jak <xref:System.Int32> (słowo kluczowe języka c#: `int` ), uzyskują się ostatecznie z jednego typu podstawowego, który jest <xref:System.Object> (słowo kluczowe języka c#: `object` ). Ta ujednolicona hierarchia typów jest nazywana [systemem common Type System](../standard/common-type-system.md) (CTS). Aby uzyskać więcej informacji na temat dziedziczenia w języku C#, zobacz [dziedziczenie](programming-guide/classes-and-structs/inheritance.md).  
  
- Każdy typ w CTS jest zdefiniowany jako *Typ wartości* lub *typ referencyjny*. Obejmuje to wszystkie niestandardowe typy w bibliotece klas .NET, a także własne typy zdefiniowane przez użytkownika. Typy, które definiujesz za pomocą `struct` `enum` słowa kluczowego or, są typami wartości. Aby uzyskać więcej informacji na temat typów wartości, zobacz [typy wartości](language-reference/builtin-types/value-types.md). Typy zdefiniowane za pomocą słowa kluczowego [Class](language-reference/keywords/class.md) to typy odwołań. Aby uzyskać więcej informacji na temat typów referencyjnych, zobacz [klasy](programming-guide/classes-and-structs/classes.md). Typy odwołań i typy wartości mają różne reguły czasu kompilacji i inne zachowanie w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

- [Typy struktur](language-reference/builtin-types/struct.md)
- [Typów wyliczeniowych](language-reference/builtin-types/enum.md)
- [Klasy](programming-guide/classes-and-structs/classes.md)

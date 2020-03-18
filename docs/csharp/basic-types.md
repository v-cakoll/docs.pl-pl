---
title: Typy podstawowe — przewodnik po językach C#
description: Dowiedz się więcej o typach podstawowych (numerach, ciągach i obiektach) we wszystkich programach języka C#
ms.date: 10/10/2016
ms.technology: csharp-fundamentals
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: bb2177026afb2eef2e14ece0c306bfd3ffe7af39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673267"
---
# <a name="types-variables-and-values"></a>Typy, zmienne i wartości

C# jest językiem silnie typizowany. Każda zmienna i stała ma typ, podobnie jak każde wyrażenie, które oblicza wartość. Każdy podpis metody określa typ dla każdego parametru wejściowego i dla wartości zwracanej. Biblioteka klas .NET Framework definiuje zestaw wbudowanych typów numerycznych, a także bardziej złożonych typów reprezentujących szeroką gamę konstrukcji logicznych, takich jak system plików, połączenia sieciowe, kolekcje i tablice obiektów i dat. Typowy program C# używa typów z biblioteki klas, a także typów zdefiniowanych przez użytkownika, które modelują pojęcia specyficzne dla domeny problemowej programu.  
  
Informacje przechowywane w typie mogą zawierać następujące elementy:  
  
- Miejsce do magazynowania, które wymaga zmiennej typu.  
  
- Wartości maksymalne i minimalne, które może reprezentować.  
  
- Elementy członkowskie (metody, pola, zdarzenia itd.), które zawiera.  
  
- Typ podstawowy, z który dziedziczy.  
  
- Lokalizacja, w której pamięć dla zmiennych zostanie przydzielona w czasie wykonywania.  
  
- Rodzaje operacji, które są dozwolone.  
  
Kompilator używa informacji o typie, aby upewnić się, że wszystkie operacje, które są wykonywane w kodzie są *bezpieczne typu*. Na przykład jeśli zadeklarować zmienną typu [int](language-reference/builtin-types/integral-numeric-types.md), kompilator umożliwia użycie zmiennej w dodatkowo i operacji odejmowania. Jeśli spróbujesz wykonać te same operacje na zmiennej [typu bool](language-reference/builtin-types/bool.md), kompilator generuje błąd, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> Deweloperzy C i C++ należy zauważyć, że w języku C#, [bool](language-reference/builtin-types/bool.md) nie jest konwertowalny na [int](language-reference/builtin-types/integral-numeric-types.md).  
  
Kompilator osadza informacje o typie w pliku wykonywalnym jako metadane. Czas wykonywania języka wspólnego (CLR) używa tych metadanych w czasie wykonywania do dalszego zagwarantowania bezpieczeństwa typów, gdy przydziela i odzyskuje pamięć.  

## <a name="specifying-types-in-variable-declarations"></a>Określanie typów w deklaracjach zmiennych

Podczas deklarowania zmiennej lub stałej w programie, należy określić jego typ lub użyć [var](language-reference/keywords/var.md) słowa kluczowego, aby umożliwić kompilatorowi wywnioskować typ. W poniższym przykładzie przedstawiono niektóre deklaracje zmiennych, które używają zarówno wbudowanych typów numerycznych, jak i złożonych typów zdefiniowanych przez użytkownika:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Typy parametrów metody i wartości zwracane są określone w podpisie metody. Następujący podpis pokazuje metodę, która wymaga [int](language-reference/builtin-types/integral-numeric-types.md) jako argument wejściowy i zwraca ciąg:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Po zadeklarowaniu zmiennej nie można jej ponownie zadeklarować przy nowym typie i nie można jej przypisać wartości, która nie jest zgodna z jej zadeklarowanym typem. Na przykład nie można zadeklarować [int,](language-reference/builtin-types/integral-numeric-types.md) a następnie `true`przypisać mu wartość logiczną . Jednak wartości mogą być konwertowane na inne typy, na przykład, gdy są one przypisane do nowych zmiennych lub przekazywane jako argumenty metody. *Konwersja typu,* która nie powoduje utraty danych jest wykonywana automatycznie przez kompilator. Konwersja, która może spowodować utratę danych wymaga *rzutowania* w kodzie źródłowym.

Aby uzyskać więcej informacji, zobacz [Konwersje rzutowania i typu](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Typy wbudowane

C# zawiera standardowy zestaw wbudowanych typów liczbowych do reprezentowania liczb całkowitych, wartości zmiennoprzecinkowych, wyrażeń logicznych, znaków tekstowych, wartości dziesiętnych i innych typów danych. Istnieją również wbudowane **typy ciągów** i **obiektów.** Są one dostępne do użycia w dowolnym programie C#. Aby uzyskać pełną listę wbudowanych typów, zobacz [Typy wbudowane](language-reference/builtin-types/built-in-types.md).
  
## <a name="custom-types"></a>Typy niestandardowe

Do tworzenia własnych typów niestandardowych należy użyć konstrukcji [struct](language-reference/keywords/class.md), [class](language-reference/keywords/class.md), [interface](language-reference/keywords/interface.md)i [enum.](language-reference/builtin-types/enum.md) Biblioteka klas .NET Framework sama w sobie jest zbiorem typów niestandardowych dostarczonych przez firmę Microsoft, których można używać we własnych aplikacjach. Domyślnie najczęściej używane typy w bibliotece klas są dostępne w dowolnym programie C#. Inne stają się dostępne tylko wtedy, gdy jawnie dodać odwołanie do projektu do zestawu, w którym są zdefiniowane. Po kompilator ma odwołanie do zestawu, można zadeklarować zmienne (i stałe) typów zadeklarowanych w tym zestawie w kodzie źródłowym.
  
## <a name="generic-types"></a>Typy ogólne

Typ może być zadeklarowany z co najmniej jeden *parametr typu,* które służą jako symbol zastępczy dla rzeczywistego typu *(typ betonu),* który kod klienta zapewni podczas tworzenia wystąpienia typu. Takie typy są nazywane *typami rodzajowymi*. Na przykład typ <xref:System.Collections.Generic.List%601> .NET Framework ma jeden parametr typu, który zgodnie z konwencją otrzymuje nazwę *T*. Podczas tworzenia wystąpienia typu należy określić typ obiektów, które będzie zawierać na przykład ciąg:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Użycie parametru type umożliwia ponowne użycie tej samej klasy do przechowywania dowolnego typu elementu, bez konieczności konwertowania każdego elementu na [obiekt.](language-reference/builtin-types/reference-types.md#the-object-type) Ogólne klasy kolekcji są nazywane *kolekcje silnie typizowane,* ponieważ kompilator zna określony typ elementów kolekcji i może wywołać błąd w `strings` czasie kompilacji, jeśli na przykład spróbujesz dodać liczbę całkowitą do obiektu w poprzednim przykładzie. Aby uzyskać więcej informacji, zobacz [Generyk .](programming-guide/generics/index.md)

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Typy niejawne, typy anonimowe i typy krotki

Jak wspomniano wcześniej, można niejawnie wpisywać zmienną lokalną (ale nie członków klasy) za pomocą [var](language-reference/keywords/var.md) słowa kluczowego. Zmienna nadal odbiera typ w czasie kompilacji, ale typ jest dostarczany przez kompilator. Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
W niektórych przypadkach jest niewygodne, aby utworzyć nazwany typ dla prostych zestawów powiązanych wartości, które nie mają zamiaru przechowywać lub przekazać poza granicami metody. W tym celu można utworzyć *typy anonimowe.* Aby uzyskać więcej informacji, zobacz [Typy anonimowe](programming-guide/classes-and-structs/anonymous-types.md).

Często chcesz zwrócić więcej niż jedną wartość z metody. Można utworzyć *typy krotki,* które zwracają wiele wartości w wywołaniu jednej metody. Aby uzyskać więcej informacji, zobacz [Krotek](tuples.md).

## <a name="the-common-type-system"></a>Wspólny system typu

Ważne jest, aby zrozumieć dwa podstawowe punkty dotyczące systemu typów w .NET Framework:  
  
- Popiera zasadę dziedziczenia. Typy mogą pochodzić od innych typów, *zwanych typami podstawowymi*. Typ pochodny dziedziczy (z pewnymi ograniczeniami) metody, właściwości i inne elementy członkowskie typu podstawowego. Typ podstawowy może z kolei pochodzić z innego typu, w którym to przypadku typu pochodnego dziedziczy elementy członkowskie obu typów podstawowych w hierarchii dziedziczenia. Wszystkie typy, w tym wbudowane typy <xref:System.Int32> liczbowe, `int`takie jak (C# keyword: ), <xref:System.Object> pochodzą ostatecznie `object`z jednego typu podstawowego, który jest (c# słowo kluczowe: ). Ta ujednolicona hierarchia typów jest nazywana [wspólnym systemem typów](../standard/common-type-system.md) (CTS). Aby uzyskać więcej informacji na temat dziedziczenia w języku C#, zobacz [Dziedziczenie](programming-guide/classes-and-structs/inheritance.md).  
  
- Każdy typ w CTS jest zdefiniowany jako *typ wartości* lub *typ odwołania*. Obejmuje to wszystkie typy niestandardowe w bibliotece klas .NET, a także własne typy zdefiniowane przez użytkownika. Typy zdefiniowane przy użyciu `struct` `enum` słowa kluczowego lub są typami wartości. Aby uzyskać więcej informacji na temat typów wartości, zobacz [Typy wartości](language-reference/builtin-types/value-types.md). Typy zdefiniowane przy użyciu słowa kluczowego [klasy](language-reference/keywords/class.md) są typami odwołań. Aby uzyskać więcej informacji na temat typów odwołań, zobacz [Klasy](programming-guide/classes-and-structs/classes.md). Typy odwołań i typy wartości mają różne reguły czasu kompilacji i różne zachowanie w czasie wykonywania.

## <a name="see-also"></a>Zobacz też

- [Typy konstrukcji](language-reference/builtin-types/struct.md)
- [Typy wyliczania](language-reference/builtin-types/enum.md)
- [Klasy](programming-guide/classes-and-structs/classes.md)

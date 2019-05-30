---
title: Typy podstawowe — Przewodnik po języku C#
description: Dowiedz się więcej o podstawowych typów (wartości numeryczne, ciągi i obiekt) we wszystkich programach języka C#
ms.date: 10/10/2016
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: a1b842747799fcc8fcb64ecf92d334342b963fa1
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300007"
---
# <a name="types-variables-and-values"></a>Typy, zmienne i wartości

C# jest językiem jednoznacznym. Każda zmienna i stała ma typ, podobnie jak każde wyrażenie, którego wynikiem jest wartość. Każdy podpis metody Określa typ dla każdego parametru wejściowego oraz wartość zwracaną. Biblioteka klas .NET Framework definiuje zestaw wbudowanych typów liczbowych, jak również bardziej złożonych typów, które reprezentują szeroką gamę konstrukcji logicznych, takich jak system plików, połączenia sieciowe, kolekcje i tablice obiektów i daty. Typowy program C# korzysta z typów z biblioteki klas, a także typy zdefiniowane przez użytkownika, które modelują koncepcje, które są specyficzne dla programu dziedziny problemu.  
  
Informacje przechowywane w typie mogą być następujące:  
  
- Wymagającego zmiennej typu miejsca do magazynowania.  
  
- Wartości maksymalne i minimalne, które może reprezentować.  
  
- Członkowie (metody, pola, zdarzenia i tak dalej), które zawiera.  
  
- Typ podstawowy, który dziedziczy.  
  
- Lokalizacja, w której w czasie wykonywania, w którym będzie można przydzielić pamięci dla zmiennych.  
  
- Rodzaje operacji, które są dozwolone.  
  
Kompilator używa informacji o typie, aby upewnić się, że wszystkie operacje, które są wykonywane w kodzie są *bezpieczny*. Na przykład, jeśli zadeklarować zmienną typu [int](language-reference/keywords/int.md), kompilator umożliwi dodatkowo użycia zmiennej operacjach dodawania i odejmowania. Jeśli próbujesz wykonać te same operacje na zmiennej typu [bool](language-reference/keywords/bool.md), kompilator generuje błąd, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> Programiści C i C++, zwróć uwagę, że w języku C# [bool](language-reference/keywords/bool.md) nie jest konwertowany na [int](language-reference/keywords/int.md).  
  
Kompilator osadza informacje o typie pliku wykonywalnego jako metadane. Środowisko uruchomieniowe języka wspólnego (CLR) używa tych metadanych w czasie wykonywania do dalszego gwarantuje bezpieczeństwo typów, gdy przydziela i przejmuje pamięć.  

## <a name="specifying-types-in-variable-declarations"></a>Określanie typów w deklaracjach zmiennych

Kiedy Deklarujesz zmienną lub stałą w programie, należy określić jej typ lub użyć [var](language-reference/keywords/var.md) — słowo kluczowe, aby umożliwić kompilatorowi wydedukować typ. Poniższy przykład pokazuje kilka deklaracji zmiennych, korzystających z wbudowanych typów liczbowych i złożonych typów zdefiniowanych przez użytkownika:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Typy parametrów metody i wartości zwracane są określone w oznaczeniu metody. Następująca sygnatura przedstawia metodę, która wymaga [int](language-reference/keywords/int.md) jako argument wejściowy i zwraca ciąg:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Po zadeklarowaniu zmiennej nie może być ponownie zadeklarowany z nowym typem i nie można przypisać wartość, która nie jest zgodna z deklarowanym typem. Na przykład nie można zadeklarować [int](language-reference/keywords/int.md) a następnie przypisać jej wartości logicznej [true](language-reference/keywords/true-literal.md). Jednakże wartości można przekonwertować do innych typów, na przykład gdy są one przypisane do nowych zmiennych lub przekazywane jako argumenty tej metody. A *konwersja typu* która nie powoduje utraty danych jest realizowane automatycznie przez kompilator. Wymaga konwersji, która może spowodować utratę danych *rzutowania* w kodzie źródłowym.

Aby uzyskać więcej informacji, zobacz [konwersje rzutowania i typ](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Typy wbudowane

C# zawiera standardowy zestaw wbudowanych typów liczbowych do reprezentowania liczb całkowitych, pływające wartości punktów, wyrażenia logiczne, znaki tekstowe, wartości dziesiętne i innych typów danych. Dostępne są również wbudowane **ciąg** i **obiektu** typów. Są one dostępne do użycia w dowolnym programie C#. Aby dowiedzieć się więcej o wbudowanych typów, zobacz [tabelę odwołań dla typów](language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Niestandardowe typy

Możesz użyć [struktury](language-reference/keywords/class.md), [klasy](language-reference/keywords/class.md), [interfejsu](language-reference/keywords/interface.md), i [wyliczenia](language-reference/keywords/enum.md) konstrukcji do tworzenia własnych typach niestandardowych. Sama biblioteka klas .NET Framework jest kolekcją typów niestandardowych dostarczonych przez firmę Microsoft, którego można używać we własnych aplikacjach. Domyślnie najczęściej używane typy w bibliotece klas są dostępne w dowolnym programie C#. Inne stają się dostępne tylko wtedy, gdy użytkownik jawnie doda odwołanie do zestawu, w której są zdefiniowane. Gdy kompilator będzie zawierać odwołanie do zestawu, można zadeklarować zmienne (i stałe) typy zadeklarowane w tym Zgromadzeniu w kodzie źródłowym.
  
## <a name="generic-types"></a>Typy ogólne

Typ może być zadeklarowany z co najmniej jeden *parametry typu* obsługujących jako symbolu zastępczego dla rzeczywistego typu ( *konkretne typu*), kod klienta zapewni podczas tworzenia wystąpienia typu. Typy takie są nazywane *typów ogólnych*. Na przykład typ .NET Framework <xref:System.Collections.Generic.List%601> ma jeden parametr typu, który zgodnie z Konwencją, otrzymuje nazwę *T*. Podczas tworzenia wystąpienia typu, należy określić typ obiektów, które zawierać będzie lista, przykładowo ciąg:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
Użyj parametru typu sprawia, że można ponownie użyć tej samej klasy do utrzymania jakiegokolwiek typu elementu, bez konieczno ści konwersji każdego elementu na [obiektu](language-reference/keywords/object.md). Klasy ogólne kolekcji są nazywane *kolekcjami jednoznacznymi* ponieważ kompilator zna określony typ elementów kolekcji i może zgłosić błąd w czasie kompilacji, jeśli, na przykład spróbujesz dodać liczbę całkowitą do `strings` obiekt w poprzednim przykładzie. Aby uzyskać więcej informacji, zobacz [ogólne](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Typy niejawne, anonimowe i typy krotek

Jak wspomniano wcześniej, można niejawnie wpisać zmienną lokalną (ale nie elementy klas) za pomocą [var](language-reference/keywords/var.md) — słowo kluczowe. Zmienna wciąż otrzymuje typ w czasie kompilacji, ale typ jest dostarczany przez kompilator. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
W niektórych przypadkach jest wygodne, aby tworzyć nazwany typ dla prostych zestawów powiązanych wartości, które nie będą przechowywane lub przekazywane poza granice metody. Możesz utworzyć *typy anonimowe* do tego celu. Aby uzyskać więcej informacji, zobacz [typy anonimowe](programming-guide/classes-and-structs/anonymous-types.md).

Jest to często mają być zwracane więcej niż jedną wartość z metody. Możesz utworzyć *typy krotki* wiele wartości zwracanych w pojedynczym wywołaniu metody. Aby uzyskać więcej informacji, zobacz [krotki](tuples.md)

## <a name="the-common-type-system"></a>Wspólny system typów

Jest to ważne, aby zrozumieć dwa podstawowe punkty o systemie typu w programie .NET Framework:  
  
- Obsługuje zasady dziedziczenia. Typy mogą pochodzić od innych typów nazywanych *typy podstawowe*. Typ pochodny dziedziczy (z pewnymi ograniczeniami) metody, właściwości i inne elementy członkowskie typu podstawowego. Typ podstawowy z kolei może pochodzić od innego typu, w którym przypadku typ pochodny dziedziczy członków obu typów podstawowych w hierarchii dziedziczenia. Wszystkie typy, w tym wbudowane typy liczbowe, takie jak <xref:System.Int32> (— słowo kluczowe języka C#: `int`), pochodzi ostatecznie z jednego typu podstawowego, który jest <xref:System.Object> (— słowo kluczowe języka C#: `object`). Ta ujednolicona hierarchia typu jest nazywany [wspólny system typów](../standard/common-type-system.md) (CTS). Aby uzyskać więcej informacji dotyczących dziedziczenia w C#, zobacz [dziedziczenia](programming-guide/classes-and-structs/inheritance.md).  
  
- Każdy typ w CTS jest zdefiniowany jako *typu wartości* lub *odwołania do typu*. Obejmuje to wszystkie niestandardowe typy w bibliotece klas programu .NET Framework, a także typy własne zdefiniowane przez użytkownika. Typy, które są definiowane za pomocą [struktury](language-reference/keywords/struct.md) — słowo kluczowe to typy wartości; wszystkie wbudowane typy liczbowe są **struktury**. Aby uzyskać więcej informacji na temat typów wartości, zobacz [struktury](structs.md). Typy, które są definiowane za pomocą [klasy](language-reference/keywords/class.md) słów kluczowych to odwołanie do typów. Aby uzyskać więcej informacji na temat typów referencyjnych, zobacz [klasy](classes.md). Typy odwołań i typy wartości mają różne zasady czasu kompilacji i różny sposób w czasie wykonywania.

## <a name="see-also"></a>Zobacz także

- [Struktury](structs.md)
- [Klasy](classes.md)

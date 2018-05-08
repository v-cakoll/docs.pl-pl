---
title: Typy podstawowe — przewodnik C#
description: Dowiedz się więcej o podstawowych typów (wartości numeryczne, ciągi i obiektów) we wszystkich programach języka C#
ms.date: 10/10/2016
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 2e62a461e41f4172bd6dd512a71babb998924978
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="types-variables-and-values"></a>Typy, zmiennych i wartości  
C# to silnie typizowane język. Każdy zmiennej i stałej ma typ, tak jak w przypadku każdego wyrażenie obliczane do wartości. Każdy podpis metody Określa typ każdego parametru wejściowego i dla wartości zwracanej. Biblioteka klas programu .NET Framework definiuje zestaw wbudowane typy liczbowe, a także bardziej złożone typy, które reprezentują szerokiej gamy konstrukcje logicznych, takich jak system plików, połączeń sieciowych, kolekcji i tablic obiektów i daty. Typowy C# program korzysta z typów z biblioteki klas, a także typy zdefiniowane przez użytkownika, które modelu pojęcia, które są specyficzne dla domeny problemu programu.  
  
Informacje przechowywane w typie mogą być następujące:  
  
-   Miejsce do magazynowania wymaga zmiennej typu.  
  
-   Maksymalne i minimalne wartości reprezentujących przez go.  
  
-   Elementy członkowskie (metody, pola, zdarzeń i tak dalej), które zawiera.  
  
-   Typ podstawowy, w którym on dziedziczy.  
  
-   Lokalizacja, w którym zostaną przydzielone pamięci dla zmiennych w czasie wykonywania.  
  
-   Rodzaje operacji, które są dozwolone.  
  
Kompilator używa informacji o typie, aby upewnić się, że wszystkie operacje, które są wykonywane w kodzie są *safe typu*. Na przykład, jeśli zadeklarować zmiennej typu [int](language-reference/keywords/int.md), kompilator umożliwia także użyć zmiennej i odejmowania operacji. Próba wykonania tych operacji tego samego na zmienną typu [bool](language-reference/keywords/bool.md), kompilator generuje błąd, jak pokazano w poniższym przykładzie:  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
>  Deweloperzy C i C++, zwróć uwagę, że w języku C# [bool](language-reference/keywords/bool.md) nie jest możliwe do przekonwertowania na [int](language-reference/keywords/int.md).  
  
Kompilator osadza informacje o typie w pliku wykonywalnego jako metadanych. Środowisko uruchomieniowe języka wspólnego (CLR) używa tych metadanych w czasie wykonywania w celu dalszego zagwarantowania bezpieczeństwa typu przydziela i zwraca pamięci.  

## <a name="specifying-types-in-variable-declarations"></a>Określanie typów w deklaracjach zmiennych  
Gdy zadeklarować zmiennej lub stała w programie, należy określić jego typ lub użyj [var](language-reference/keywords/var.md) — słowo kluczowe, aby umożliwić kompilatora wnioskować o typie. W poniższym przykładzie przedstawiono niektóre deklaracji zmiennych, które używają zarówno wbudowane typy liczbowe, jak i złożone typy danych zdefiniowane przez użytkownika:  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Typy parametrów metod i wartości zwracane są określone w podpisie metody. Następująca sygnatura zawiera metodę, która wymaga [int](language-reference/keywords/int.md) jako argument wejściowy i zwraca wartość typu ciąg:  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Po zadeklarowaniu zmiennej nie może być ponownie zadeklarowany z nowym typem i nie można przypisać wartość, która jest niezgodna z deklarowanym typem. Na przykład nie można zadeklarować [int](language-reference/keywords/int.md) , a następnie przypisz jej wartość logiczną [true](language-reference/keywords/true.md). Jednak można konwertować wartości dla innych typów, na przykład gdy są one przypisane do nowe zmienne lub przekazywane jako argumenty metody. A *konwersja typu* tego ma nie Przyczyna utraty danych jest realizowane automatycznie przez kompilator. Wymaga konwersji, która może spowodować utratę danych *rzutowania* w kodzie źródłowym. 

Aby uzyskać więcej informacji, zobacz [konwersje rzutowania i typ](programming-guide/types/casting-and-type-conversions.md).
 
## <a name="built-in-types"></a>Typy wbudowane
C# zawiera standardowy zestaw wbudowanych typów numerycznych do reprezentowania liczb całkowitych, zmiennoprzecinkowych wartości, wyrażeń logicznych, znaki tekstu, wartości dziesiętnych i innymi typami danych. Istnieją również wbudowane **ciąg** i **obiektu** typów. Są one dostępne do użycia w programach języka C#. Aby uzyskać więcej informacji o wbudowanych typów, zobacz [tabeli odwołań dla typów](language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Niestandardowe typy  
Możesz użyć [struktury](language-reference/keywords/class.md), [klasy](language-reference/keywords/class.md), [interfejsu](language-reference/keywords/interface.md), i [wyliczenia](language-reference/keywords/enum.md) konstrukcji, aby utworzyć własne niestandardowe typy. Biblioteka klas programu .NET Framework sam jest kolekcją typów niestandardowych dostarczanych przez firmę Microsoft, używanego w aplikacjach. Domyślnie najczęściej używane typy w bibliotece klas są dostępne w programach języka C#. Inne stają się dostępne tylko wtedy, gdy jawnie dodać odwołanie projektu do zestawu, w którym jest zdefiniowany. Po kompilator ma odwołanie do zestawu, mogą zadeklarować zmienne (i stałych) typów zadeklarowany w tym zestawie w kodzie źródłowym. 
  
## <a name="generic-types"></a>Typy ogólne  
Typ mogą być deklarowane z co najmniej jednym *parametry typu* obsługujących jako symbol zastępczy rzeczywisty typ ( *specyficzne typu*) czy kod klienta zapewni podczas tworzenia wystąpienia typu. Takie typy są nazywane *typów ogólnych*. Na przykład typ .NET Framework <xref:System.Collections.Generic.List%601> ma jeden parametr typu, który przez Konwencję o nazwie *T*. Podczas tworzenia wystąpienia typu, należy określić typ obiektu, który będzie zawierać listę, na przykład ciąg:  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)] 
  
Użyj parametru typu umożliwia ponowne użycie tej samej klasy, aby pomieścić dowolnego typu elementu, bez konieczności Konwertuj każdy element na [obiektu](language-reference/keywords/object.md). Klasy kolekcji ogólnych są nazywane *kolekcje silnie typizowane* ponieważ kompilator zna określonego typu elementów w kolekcji i może zgłaszać błąd w czasie kompilacji Jeśli, na przykład próby dodania całkowitą do `strings` obiektu w poprzednim przykładzie. Aby uzyskać więcej informacji, zobacz [ogólne](programming-guide/generics/index.md). 

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Niejawne typów, typy anonimowe i spójnej kolekcji typów  
Jak wspomniano wcześniej, można niejawnie wpisać zmiennej lokalnej (ale nie elementów członkowskich klasy) przy użyciu [var](language-reference/keywords/var.md) — słowo kluczowe. Zmienna nadal otrzymuje typu w czasie kompilacji, ale podano typ przez kompilator. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
W niektórych przypadkach jest niewygodne do utworzenia nazwanego typu prostego zestawów powiązanych wartości, które będą przechowywać lub Przekaż poza granice — metoda. Można utworzyć *typy anonimowe* w tym celu. Aby uzyskać więcej informacji, zobacz [typy anonimowe](programming-guide/classes-and-structs/anonymous-types.md).

Są często do więcej niż jedną wartość zwracana z metody. Można utworzyć *typu krotki* które zwracają wielu wartości w wywołaniu pojedynczej metody. Aby uzyskać więcej informacji, zobacz [krotek](tuples.md)

## <a name="the-common-type-system"></a>Wspólny system typów  
Należy wziąć pod uwagę dwa punkty podstawowe informacje o systemie typu w programie .NET Framework:  
  
-   Obsługuje zasady dziedziczenia. Typy może pochodzić od innych typów o nazwie *typy podstawowe*. Typ pochodny dziedziczy (z pewnymi ograniczeniami), metody, właściwości i innych elementach członkowskich typu podstawowego. Typ podstawowy z kolei może pochodzić od innego typu, w których przypadku typ pochodny dziedziczy członkami obu typów podstawowych w hierarchii dziedziczenia. Wszystkich typów, w tym wbudowane typy liczbowe, takie jak <xref:System.Int32> (C# — słowo kluczowe: `int`), pochodzi ostatecznie z jednego typu podstawowego, który jest <xref:System.Object> (C# — słowo kluczowe: `object`). Ta hierarchia ujednoliconego typu jest nazywana [wspólny system typów](../standard/common-type-system.md) (CTS). Aby uzyskać więcej informacji na temat dziedziczenia w języku C#, zobacz [dziedziczenia](programming-guide/classes-and-structs/inheritance.md).  
  
-   Każdy typ w CTS jest zdefiniowany jako *typu wartości* lub *zawierają odwołania do typu*. W tym wszystkich niestandardowych typów w bibliotece klas programu .NET Framework, a także własnych typów zdefiniowanych przez użytkownika. Typy zdefiniowane przez użytkownika za pomocą [struktury](language-reference/keywords/struct.md) — słowo kluczowe są typy wartości; są wbudowane typy liczbowe **struktury**. Aby uzyskać więcej informacji na temat typów wartości, zobacz [struktury](structs.md). Typy zdefiniowane przez użytkownika za pomocą [klasy](language-reference/keywords/class.md) — słowo kluczowe są odwołania typów. Aby uzyskać więcej informacji na temat typów referencyjnych zobacz [klasy](classes.md). Typy odwołań i typów wartości mają różne reguły kompilacji, a inaczej w czasie wykonywania.
 
  
## <a name="see-also"></a>Zobacz także
[Struktury](structs.md)
[klas](classes.md)

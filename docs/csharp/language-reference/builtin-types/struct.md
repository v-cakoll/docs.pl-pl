---
title: Typy struktury — odwołanie do języka C#
ms.date: 04/21/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: dbe9b47625589de834b7a8021640885ca0920b96
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "82021271"
---
# <a name="structure-types-c-reference"></a>Typy struktury (odwołanie do języka C#)

*Typ struktury* (lub *typ struktury*) jest [typem wartości,](value-types.md) który może hermetyzować dane i powiązane funkcje. Słowo `struct` kluczowe służy do definiowania typu struktury:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Typy struktur mają *semantykę wartości*. Oznacza to, że zmienna typu struktury zawiera wystąpienie typu. Domyślnie wartości zmiennych są kopiowane przy przypisywaniu, przekazywaniu argumentu do metody i zwracaniu wyniku metody. W przypadku zmiennej typu struktury kopiowane jest wystąpienie typu. Aby uzyskać więcej informacji, zobacz [Typy wartości](value-types.md).

Zazwyczaj typy struktury służy do projektowania małych typów zorientowanych na dane, które zapewniają niewielkie lub żadne zachowanie. Na przykład .NET używa typów struktury do reprezentowania liczby [(zarówno liczby całkowitej,](integral-numeric-types.md) jak i [rzeczywistej),](floating-point-numeric-types.md) [wartości logicznej,](bool.md) [znaku Unicode,](char.md) [wystąpienia czasu](xref:System.DateTime). Jeśli koncentrujesz się na zachowaniu typu, rozważ zdefiniowanie [klasy](../keywords/class.md). Typy klas mają *semantykę odwołań*. Oznacza to, że zmienna typu klasy zawiera odwołanie do wystąpienia typu, a nie samego wystąpienia.

Ponieważ typy struktur mają semantykę wartości, zaleca się definiowanie typów struktur *niezmiennych.*

## <a name="readonly-struct"></a>`readonly`Struct

Począwszy od języka C# 7.2, można użyć `readonly` modyfikatora, aby zadeklarować, że typ struktury jest niezmienne:

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

Wszystkie elementy członkowskie `readonly` danych struktury muszą być tylko do odczytu w następujący sposób:

- Każda deklaracja pola musi mieć [ `readonly` modyfikator](../keywords/readonly.md)
- Wszelkie właściwości, w tym te zaimplementowane automatycznie, muszą być

Gwarantuje to, że `readonly` żaden element członkowski struktury modyfikuje stan struktury.

> [!NOTE]
> `readonly` W strukturze element członkowski danych typu odwołania modyfikowalne nadal można mutować swój własny stan. Na przykład nie można zastąpić <xref:System.Collections.Generic.List%601> wystąpienia, ale można dodać do niego nowe elementy.

## <a name="readonly-instance-members"></a>`readonly`elementy członkowskie wystąpienia

Począwszy od języka C# 8.0, można również użyć `readonly` modyfikatora do deklarowania, że element członkowski wystąpienia nie modyfikuje stanu struktury. Jeśli nie można zadeklarować cały `readonly`typ struktury `readonly` jako , użyj modyfikatora, aby oznaczyć elementy członkowskie wystąpienia, które nie modyfikują stan struktury. W `readonly` strukturze każdy element członkowski `readonly`instancji jest niejawnie .

W `readonly` obrębie elementu członkowskiego wystąpienia nie można przypisać do pól wystąpienia struktury. Jednak `readonly` członek może wywołać`readonly` non-element członkowski. W takim przypadku kompilator tworzy kopię wystąpienia struktury`readonly` i wywołuje non-element członkowski na tej kopii. W rezultacie oryginalne wystąpienie struktury nie jest modyfikowany.

Zazwyczaj `readonly` modyfikator jest stosowany do następujących rodzajów elementów członkowskich wystąpienia:

- Metody:

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  `readonly` Modyfikator można również zastosować do metod, które <xref:System.Object?displayProperty=nameWithType>zastępują metody zadeklarowane w:

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- właściwości i indeksatory:

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  Jeśli musisz zastosować `readonly` modyfikator do obu akcesorów właściwości lub indeksatora, zastosuj go w oświadczeniu właściwości lub indeksatora.

  > [!NOTE]
  > Kompilator deklaruje `get` akcesor [właściwości automatycznie implementowane](../../programming-guide/classes-and-structs/auto-implemented-properties.md) jako `readonly`, `readonly` niezależnie od obecności modyfikatora w deklaracji właściwości.

`readonly` Modyfikator nie może być stosowany do statycznych elementów członkowskich typu struktury.

Kompilator może korzystać `readonly` z modyfikatora do optymalizacji wydajności. Aby uzyskać więcej informacji, zobacz [Pisanie bezpiecznego i wydajnego kodu języka C#.](../../write-safe-efficient-code.md)

## <a name="limitations-with-the-design-of-a-structure-type"></a>Ograniczenia związane z projektowaniem typu konstrukcji

Podczas projektowania typu struktury, masz takie same możliwości jak w przypadku typu [klasy,](../keywords/class.md) z następującymi wyjątkami:

- Nie można zadeklarować konstruktora bez parametrów. Każdy typ struktury już zapewnia niejawne bez parametrów konstruktora, który tworzy [wartość domyślną](default-values.md) typu.

- Nie można zainicjować pola wystąpienia lub właściwości w jego deklaracji. Można jednak zainicjować pole [statyczne](../keywords/static.md) lub [const](../keywords/const.md) lub właściwość statyczną w jego deklaracji.

- Konstruktor typu struktury musi zainicjować wszystkie pola wystąpienia typu.

- Typ struktury nie może dziedziczyć z innej klasy lub typu struktury i nie może być podstawą klasy. Jednak typ struktury można zaimplementować [interfejsy](../keywords/interface.md).

- Nie można zadeklarować [finalizatora](../../programming-guide/classes-and-structs/destructors.md) w ramach typu struktury.

## <a name="instantiation-of-a-structure-type"></a>Tworzenie wystąpienia typu struktury

W języku C#należy zainicjować zadeklarowaną zmienną, zanim będzie można jej użyć. Ponieważ zmienna typu struktury nie `null` może być (chyba że jest to zmienna [typu wartości nullable),](nullable-value-types.md)należy utworzyć wystąpienie odpowiedniego typu. Istnieje kilka sposobów, aby to zrobić.

Zazwyczaj można utworzyć wystąpienia typu struktury, wywołując odpowiedni konstruktor z operatorem. [`new`](../operators/new-operator.md) Każdy typ struktury ma co najmniej jeden konstruktor. Jest to niejawny konstruktor bez parametrów, który tworzy [wartość domyślną](default-values.md) typu. Można również użyć [wyrażenia wartości domyślnej,](../operators/default.md) aby utworzyć wartość domyślną typu.

Jeśli wszystkie pola wystąpienia typu struktury są dostępne, można również `new` utworzyć wystąpienia bez operatora. W takim przypadku należy zainicjować wszystkie pola wystąpienia przed pierwszym użyciem wystąpienia. W poniższym przykładzie pokazano, jak to zrobić:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

W przypadku [wbudowanych typów wartości](value-types.md#built-in-value-types)użyj odpowiednich literałów, aby określić wartość typu.

## <a name="passing-structure-type-variables-by-reference"></a>Przekazywanie zmiennych typu struktury przez odwołanie

Po przedaniu zmiennej typu struktury do metody jako argument lub zwracaniu wartości typu struktury z metody, kopiowane jest całe wystąpienie typu struktury. Może to mieć wpływ na wydajność kodu w scenariuszach o wysokiej wydajności, które obejmują duże typy struktur. Można uniknąć kopiowania wartości, przekazując zmienną typu struktury przez odwołanie. Użyj [`ref`](../keywords/ref.md#passing-an-argument-by-reference)modyfikatorów parametrów , [`out`](../keywords/out-parameter-modifier.md)lub [`in`](../keywords/in-parameter-modifier.md) metody, aby wskazać, że argument musi być przekazywany przez odwołanie. Użyj [ref zwraca,](../../programming-guide/classes-and-structs/ref-returns.md) aby zwrócić wynik metody przez odwołanie. Aby uzyskać więcej informacji, zobacz [Pisanie bezpiecznego i wydajnego kodu języka C#.](../../write-safe-efficient-code.md)

## <a name="ref-struct"></a>`ref`Struct

Począwszy od C# 7.2, `ref` można użyć modyfikatora w deklaracji typu struktury. `ref` Wystąpienia typu struktury są przydzielane na stosie i nie można uciec do zarządzanego stosu. Aby upewnić się, że kompilator ogranicza użycie `ref` typów struktury w następujący sposób:

- Struktura `ref` nie może być typem elementu tablicy.
- Struktura `ref` nie może być zadeklarowanym typem pola klasy lub`ref` niestrukturą.
- Struktura `ref` nie można zaimplementować interfejsów.
- Nie `ref` można zapakować struktury <xref:System.ValueType?displayProperty=nameWithType> do <xref:System.Object?displayProperty=nameWithType>lub .
- Struktura `ref` nie może być argumentem typu.
- Zmienna `ref` struktury nie może zostać [przechwycona przez wyrażenie lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) lub funkcję [lokalną](../../programming-guide/classes-and-structs/local-functions.md).
- Zmiennej `ref` struktury nie można użyć [`async`](../keywords/async.md) w metodzie. Można jednak użyć `ref` zmiennych struktury w metodach synchronicznych, na <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>przykład w tych, które zwracają lub .
- Zmiennej `ref` struktury nie można używać w [iteratorach](../../iterators.md).

Zazwyczaj typ struktury `ref` jest definiowany, gdy potrzebny jest typ, `ref` który zawiera również elementy członkowskie danych typów struktury:

[!code-csharp[ref struct](snippets/StructType.cs#RefStruct)]

Aby zadeklarować `ref` strukturę jako `readonly` `ref` `readonly` `ref` [`readonly`](#readonly-struct), połączyć i modyfikatorów w deklaracji typu (modyfikator musi pochodzić przed modyfikatorem):

[!code-csharp[readonly ref struct](snippets/StructType.cs#ReadonlyRef)]

W .NET przykłady `ref` struktury są <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>i .

## <a name="conversions"></a>Konwersje

Dla każdego typu struktury (z <xref:System.ValueType?displayProperty=nameWithType> wyjątkiem <xref:System.Object?displayProperty=nameWithType> [ `ref` ](#ref-struct) typów struktury), istnieje [boks i unboxing](../../programming-guide/types/boxing-and-unboxing.md) konwersji do iz typów. Istnieją również konwersje boksu i rozpakowywania między typem struktury a dowolnym interfejsem, który implementuje.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Struktury](~/_csharplang/spec/structs.md) [specyfikacji języka języka języka C#.](~/_csharplang/spec/introduction.md)

Aby uzyskać więcej informacji na temat funkcji wprowadzonych w języku C# 7.2 i nowszych, zobacz następujące uwagi dotyczące propozycji funkcji:

- [Tylko do odczytywanie struktur](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [Elementy członkowskie wystąpień tylko do odczytu](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)
- [Bezpieczeństwo czasu kompilowania dla typów zbliżonych do odwołań](~/_csharplang/proposals/csharp-7.2/span-safety.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Wskazówki dotyczące projektowania — wybór między klasą a strukturą](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Wskazówki dotyczące projektowania — projektowanie konstrukcji](../../../standard/design-guidelines/struct.md)
- [Klasy i struktury](../../programming-guide/classes-and-structs/index.md)

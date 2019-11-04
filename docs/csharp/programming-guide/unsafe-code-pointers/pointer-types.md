---
title: Typy wskaźnika — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: b9b9f145f8f2d945fa06d53efa89f5754766963f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423126"
---
# <a name="pointer-types-c-programming-guide"></a>Typy wskaźników (Przewodnik programowania w języku C#)

W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym. Deklaracja typu wskaźnika ma jedną z następujących form:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ określony przed `*` w typie wskaźnika jest nazywany **typem referent**. Tylko [Typ niezarządzany](../../language-reference/builtin-types/unmanaged-types.md) może być typem referent.

Typy wskaźnika nie dziedziczą z [obiektu](../../language-reference/builtin-types/reference-types.md) i nie istnieją konwersje między typami wskaźnika a `object`. Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania. Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.

W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika. Na przykład:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Wskaźnik nie może wskazywać odwołania lub [struktury](../../language-reference/keywords/struct.md) , która zawiera odwołania, ponieważ odwołanie do obiektu może być odzyskiwane nawet wtedy, gdy wskaźnik wskazuje go. Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.

Wartość zmiennej wskaźnika typu `myType*` jest adresem zmiennej typu `myType`. Poniżej przedstawiono przykłady deklaracji typów wskaźnika:

|Przykład|Opis|
|-------------|-----------------|
|`int* p`|`p` jest wskaźnikiem do liczby całkowitej.|
|`int** p`|`p` jest wskaźnikiem do wskaźnika do liczby całkowitej.|
|`int*[] p`|`p` to Jednowymiarowa tablica wskaźników do liczb całkowitych.|
|`char* p`|`p` jest wskaźnikiem do znaku.|
|`void* p`|`p` jest wskaźnikiem do nieznanego typu.|

Operatora pośredniego wskaźnika * można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową. Na przykład przeanalizujmy następującą deklarację:

```csharp
int* myVariable;
```

Wyrażenie `*myVariable` oznacza zmienną `int` znalezioną pod adresem zawartym w `myVariable`.

Kilka przykładów wskaźników znajduje się w tematach [stałych instrukcja](../../language-reference/keywords/fixed-statement.md) i [konwersje wskaźnika](./pointer-conversions.md). Poniższy przykład używa słowa kluczowego `unsafe` i instrukcji `fixed` i pokazuje, jak zwiększyć wewnętrzny wskaźnik.  Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić. Te przykłady muszą zostać skompilowane przy użyciu [-niebezpiecznego](../../language-reference/compiler-options/unsafe-compiler-option.md) zestawu opcji kompilatora.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Nie można zastosować operatora pośredni do wskaźnika typu `void*`. Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.

Wskaźnik może być `null`. Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.

Przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie. Rozważmy metodę, która zwraca wskaźnik do zmiennej lokalnej za pomocą `in`, `out`lub parametru `ref` lub jako wynik funkcji. Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.

W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:

|Operator/instrukcja|Zastosowanie|
|-------------------------|---------|
|`*`|Wykonuje operację wskaźnika pośredniego.|
|`->`|Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.|
|`[]`|Indeksuje wskaźnik.|
|`&`|Uzyskuje adres zmiennej.|
|`++` i `--`|Zwiększa i zmniejsza wartość wskaźnika.|
|`+` i `-`|Wykonuje operacje arytmetyczne na wskaźniku.|
|`==`, `!=`, `<`, `>`, `<=`i `>=`|Porównuje wskaźniki.|
|[operator `stackalloc`](../../language-reference/operators/stackalloc.md)|Przydziela pamięć na stosie.|
|[Instrukcja `fixed`](../../language-reference/keywords/fixed-statement.md)|Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.|

Aby uzyskać więcej informacji na temat operatorów powiązanych ze wskaźnikiem, zobacz temat [Operatory powiązane z wskaźnikiem](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [Konwersje wskaźników](pointer-conversions.md)
- [Typy](/dotnet/csharp/language-reference/keywords)
- [unsafe](../../language-reference/keywords/unsafe.md)

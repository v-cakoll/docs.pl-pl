---
title: Typy wskaźników — przewodnik po programowaniu języka C#
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 7bbfa6b2238458d3248da830cf9d6ac36551b431
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507038"
---
# <a name="pointer-types-c-programming-guide"></a>Typy wskaźników (Przewodnik programowania w języku C#)

W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym. Deklaracja typu wskaźnika ma jedną z następujących form:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ określony przed `*` typem wskaźnika nazywa **się typem referencyjnym**. Tylko [typ niezarządzany](../../language-reference/builtin-types/unmanaged-types.md) może być typem referencyjnym.

Typy wskaźników nie dziedziczą z [obiektu](../../language-reference/builtin-types/reference-types.md) i `object`między typami wskaźników nie istnieją konwersje. Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania. Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.

W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika. Przykład:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Wskaźnik nie może wskazywać na odwołanie lub [struktury,](../../language-reference/builtin-types/struct.md) która zawiera odwołania, ponieważ odwołanie do obiektu może być śmieci zbierane, nawet jeśli wskaźnik jest skierowany do niego. Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.

Wartość zmiennej wskaźnika `myType*` typu jest adresem zmiennej `myType`typu . Poniżej przedstawiono przykłady deklaracji typów wskaźnika:

|Przykład|Opis|
|-------------|-----------------|
|`int* p`|`p`jest wskaźnikiem do liczby całkowitej.|
|`int** p`|`p`jest wskaźnikiem do wskaźnika do liczby całkowitej.|
|`int*[] p`|`p`jest jednowymiarową tablicą wskaźników do liczby całkowitej.|
|`char* p`|`p`jest wskaźnikiem do char.|
|`void* p`|`p`jest wskaźnikiem do nieznanego typu.|

Operatora pośredniego wskaźnika * można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową. Na przykład przeanalizujmy następującą deklarację:

```csharp
int* myVariable;
```

Wyrażenie `*myVariable` oznacza zmienną `int` znalezioną pod adresem `myVariable`zawartym w programie .

Istnieje kilka przykładów wskaźników w tematach [stałych konwersji instrukcji](../../language-reference/keywords/fixed-statement.md) i [wskaźnika](./pointer-conversions.md). W poniższym `unsafe` przykładzie użyto słowa kluczowego i `fixed` instrukcji i pokazano, jak zwiększać wskaźnik wewnętrzny.  Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić. Te przykłady muszą być skompilowane z zestawem opcji [kompilatora -unsafe.](../../language-reference/compiler-options/unsafe-compiler-option.md)

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Nie można zastosować operatora pośredniego do `void*`wskaźnika typu . Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.

Wskaźnik może `null`być . Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.

Przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie. Należy wziąć pod uwagę metodę, która `in`zwraca `out`wskaźnik `ref` do zmiennej lokalnej za pośrednictwem , lub parametru lub jako wynik funkcji. Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.

W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:

|Operator/instrukcja|Użycie|
|-------------------------|---------|
|`*`|Wykonuje operację wskaźnika pośredniego.|
|`->`|Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.|
|`[]`|Indeksuje wskaźnik.|
|`&`|Uzyskuje adres zmiennej.|
|`++` i `--`|Zwiększa i zmniejsza wartość wskaźnika.|
|`+` i `-`|Wykonuje operacje arytmetyczne na wskaźniku.|
|`==`, `!=` `<`, `>` `<=`, , i`>=`|Porównuje wskaźniki.|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|Przydziela pamięć na stosie.|
|[`fixed`Instrukcja](../../language-reference/keywords/fixed-statement.md)|Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.|

Aby uzyskać więcej informacji na temat operatorów powiązanych ze [wskaźnikiem, zobacz Operatory powiązane ze wskaźnikiem](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [specyfikacji języka języka języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [C# Przewodnik programowania](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [Konwersje wskaźników](pointer-conversions.md)
- [Typy odwołań](../../language-reference/keywords/reference-types.md)
- [Typy wartości](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)

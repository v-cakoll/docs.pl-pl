---
title: Typy wskaźników - C# Programming Guide
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 59846affb1eea5bd9d6a80c623eab5e3aa9db87c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661081"
---
# <a name="pointer-types-c-programming-guide"></a>Typy wskaźników (Przewodnik programowania w języku C#)

W kontekście słowa kluczowego „unsafe” typ może być typem wskaźnika, typem wartości lub typem referencyjnym. Deklaracja typu wskaźnika ma jedną z następujących form:

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

Typ określony przed `*` w wskaźnik typu jest nazywana **typu Obiekt obsługujący**. Dowolne z następujących typów może być typem obiekt obsługujący:

- Dowolnego typu całkowitoliczbowego: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [bajtów](../../language-reference/builtin-types/integral-numeric-types.md), [krótki](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [długie](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).
- Wszystkie typy zmiennoprzecinkowe: [float](../../language-reference/builtin-types/floating-point-numeric-types.md), [double](../../language-reference/builtin-types/floating-point-numeric-types.md).
- [CHAR](../../language-reference/keywords/char.md).
- [wartość logiczna](../../language-reference/keywords/bool.md).
- [dziesiętna](../../language-reference/builtin-types/floating-point-numeric-types.md).
- Wszelkie [wyliczenia](../../language-reference/keywords/enum.md) typu.
- Dowolny typ wskaźnika. Dzięki temu wyrażenia takie jak `void**`.
- Dowolny typ struktury zdefiniowany przez użytkownika, który zawiera tylko pola niezarządzanych typów.

Typy wskaźnika nie dziedziczą [obiektu](../../language-reference/keywords/object.md) i nie występują konwersje między typami wskaźnika a `object`. Ponadto wskaźniki nie są obsługiwane w przypadku opakowywania i rozpakowywania. Można jednak wykonywać konwersje między różnymi typami wskaźnika oraz między typami wskaźnika a typami całkowitymi.

W przypadku deklarowania wielu wskaźników w jednej deklaracji gwiazdka (*) jest pisana razem tylko z typem podstawowym; nie jest używana jako prefiks każdej nazwy wskaźnika. Na przykład:

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

Wskaźnik nie może wskazywać odwołania ani do [struktury](../../language-reference/keywords/struct.md) zawierającej odwołania, ponieważ odwołanie do obiektu może zostać usunięte nawet wtedy, gdy jest wskazywane przez wskaźnik do niego. Moduł odśmiecania pamięci nie sprawdza, czy obiekt jest wskazywany przez jakiś wskaźnik.

Wartość zmiennej wskaźnika typu `myType*` to adres zmiennej typu `myType`. Poniżej przedstawiono przykłady deklaracji typów wskaźnika:

|Przykład|Opis|
|-------------|-----------------|
|`int* p`|`p` to wskaźnik do liczby całkowitej.|
|`int** p`|`p` to wskaźnik do wskaźnika do liczby całkowitej.|
|`int*[] p`|`p` to Jednowymiarowa tablica wskaźników do liczb całkowitych.|
|`char* p`|`p` jest wskaźnik do znaku.|
|`void* p`|`p` to wskaźnik do nieznanego typu.|

Operatora pośredniego wskaźnika * można użyć w celu uzyskania dostępu do zawartości znajdującej się w lokalizacji wskazywanej przez zmienną wskaźnikową. Na przykład przeanalizujmy następującą deklarację:

```csharp
int* myVariable;
```

Wyrażenie `*myVariable` oznacza `int` znaleziono pod adresem zawartym w zmiennej `myVariable`.

Istnieje kilka przykładów wskaźników można znaleźć w tematach [fixed Statement](../../language-reference/keywords/fixed-statement.md) i [konwersje wskaźników](../../programming-guide/unsafe-code-pointers/pointer-conversions.md). W poniższym przykładzie użyto `unsafe` — słowo kluczowe i `fixed` instrukcji i pokazuje, jak zwiększyć wartość wskaźnika wewnętrznego.  Ten kod można wkleić do funkcji Main aplikacji konsoli, aby go uruchomić. Przykłady te muszą być skompilowane z [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) zestaw opcji kompilatora.

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

Nie można zastosować operatora pośredniego do wskaźnika typu `void*`. Można jednak użyć rzutowania, aby przekonwertować wskaźnik typu void na wskaźnik dowolnego innego typu i odwrotnie.

Wskaźnik może mieć `null`. Zastosowanie operatora pośredniego do wskaźnika o wartości null powoduje użycie zachowania zdefiniowanego w implementacji.

Przekazywanie wskaźników między metodami może spowodować niezdefiniowane zachowanie. Należy wziąć pod uwagę metodę, która zwraca wskaźnik do zmiennej lokalnej za pośrednictwem `in`, `out`, lub `ref` parametru lub jako wynik funkcji. Jeśli wskaźnik został ustawiony w stałym bloku, wskazywana przez niego zmienna może już nie być stała.

W poniższej tabeli wymieniono operatory i instrukcje, które mogą wykonywać operacje na wskaźnikach w kontekście słowa kluczowego „unsafe”:

|Operator/instrukcja|Zastosowanie|
|-------------------------|---------|
|`*`|Wykonuje operację wskaźnika pośredniego.|
|`->`|Uzyskuje dostęp do elementu członkowskiego struktury za pomocą wskaźnika.|
|`[]`|Indeksuje wskaźnik.|
|`&`|Uzyskuje adres zmiennej.|
|`++` i `--`|Zwiększa i zmniejsza wartość wskaźnika.|
|`+` i `-`|Wykonuje operacje arytmetyczne na wskaźniku.|
|`==`, `!=`, `<`, `>`, `<=`, i `>=`|Porównuje wskaźniki.|
|[`stackalloc` Operator](../../language-reference/operators/stackalloc.md)|Przydziela pamięć na stosie.|
|[`fixed` Instrukcja](../../language-reference/keywords/fixed-statement.md)|Tymczasowo ustala zmienną, dzięki czemu można znaleźć ten adres.|

Aby uzyskać więcej informacji na temat wskaźnika powiązane operatorów, zobacz [wskaźnik związane z operatorów](../../language-reference/operators/pointer-related-operators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [Konwersje wskaźników](pointer-conversions.md)
- [Typy](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)

---
title: Wskaźnik związane z operatorów - C# odwołania
description: Dowiedz się więcej o C# operatorów, które można użyć podczas pracy z wskaźników.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 03d6ed19ef01be7712ff2fdde0c1be2a6673e64f
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401441"
---
# <a name="pointer-related-operators-c-reference"></a>Wskaźnik związane z operatorów (C# odwołania)

Pracować ze wskaźnikami, można używać następujących operatorów:

- Jednoargumentowy [ `&` (adresu z)](#address-of-operator-) operator: można pobrać adresu zmiennej
- Jednoargumentowy [ `*` (operację wskaźnika pośredniego)](#pointer-indirection-operator-) operator: uzyskanie zmiennej wskazywana przez wskaźnik
- [ `->` (Dostęp do elementu członkowskiego)](#pointer-member-access-operator--) i [ `[]` (dostęp do elementu)](#pointer-element-access-operator-) operatorów
- Operatory arytmetyczne [ `+`, `-`, `++`, i `--`](#pointer-arithmetic-operators)
- Operatory porównania [ `==`, `!=`, `<`, `>`, `<=`, i `>=`](#pointer-comparison-operators)

Aby uzyskać informacje dotyczące typów wskaźnika, zobacz [typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Wszelkie działania, za pomocą wskaźników wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu. Kod, który zawiera bloki niebezpieczne musi być skompilowana przy użyciu [ `-unsafe` ](../compiler-options/unsafe-compiler-option.md) — opcja kompilatora.

## <a name="address-of-operator-"></a> Operator Address-of &amp;

Jednoargumentowy `&` operator zwraca adres jego operandu:

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

Argument operacji `&` operator musi być zmienna ustalona. *Naprawiono* zmienne są zmienne, które znajdują się w lokalizacji przechowywania, które nie ma wpływu na działanie [modułu zbierającego elementy bezużyteczne](../../../standard/garbage-collection/index.md). W poprzednim przykładzie, zmienna lokalna `number` jest zmienna ustalona, ponieważ znajduje się on na stosie. Zmienne, które znajdują się w lokalizacji przechowywania, które mogą mieć wpływ moduł odśmiecania pamięci (na przykład przenieść) są nazywane *ruchome* zmiennych. Pola obiektu i elementy tablicy są przykłady ruchome zmiennych. Można uzyskać adresu zmiennej ruchome, jeśli "naprawić" lub "przypinając" je za pomocą [stałej](../keywords/fixed-statement.md) instrukcji. Uzyskanej adres jest prawidłowy tylko na czas trwania `fixed` blok instrukcji. Poniższy przykład pokazuje, jak używać `fixed` instrukcji i `&` operator:

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Nie można pobrać adresu stała lub wartość.

Aby uzyskać więcej informacji na temat zmiennych stałych i okazjonalnych zobacz [stałe i zmienne ruchome](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Plik binarny `&` oblicza operator [operator logiczny oraz](boolean-logical-operators.md#logical-and-operator-) z argumentów logicznych lub [iloczynu bitowego AND logiczne](bitwise-and-shift-operators.md#logical-and-operator-) jej całkowitego operandu.

## <a name="pointer-indirection-operator-"></a>Operatora pośredniego wskaźnika *

Jednoargumentowy operator pośredni wskaźnik `*` uzyskuje zmiennej, do którego wskazuje operand. Jest również nazywany operator wyłuskania. Argument operacji `*` operatora musi być typem wskaźnika.

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

Nie można zastosować `*` operatora wyrażenia typu `void*`.

Plik binarny `*` oblicza operator [produktu](arithmetic-operators.md#multiplication-operator-) z liczbową argumentów.

## <a name="pointer-member-access-operator--"></a>Operator dostępu do elementu członkowskiego wskaźnik ->

`->` Łączy operator [operację wskaźnika pośredniego](#pointer-indirection-operator-) i [dostęp do elementu członkowskiego](member-access-operators.md#member-access-operator-). Oznacza to jeśli `x` jest wskaźnikiem typu `T*` i `y` jest dostępny członek `T`, wyrażenie formularza

```csharp
x->y
```

odpowiada wyrażeniu

```csharp
(*x).y
```

W poniższym przykładzie pokazano użycie `->` operator:

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

Nie można zastosować `->` operatora wyrażenia typu `void*`.

## <a name="pointer-element-access-operator-"></a>Wskaźnik elementu dostępu operator w]

Wyrażenie `p` typu wskaźnika, dostęp do elementu wskaźnika w postaci `p[n]` jest oceniane jako `*(p + n)`, gdzie `n` musi być typu niejawnej konwersji `int`, `uint`, `long`, lub `ulong`. Aby uzyskać informacje o zachowanie `+` operator za pomocą wskaźników, zobacz [dodawania lub odejmowania liczb całkowitych do lub ze wskaźnika](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) sekcji.

Poniższy przykład pokazuje, jak uzyskać dostęp do elementów tablicy ze wskaźnikiem i `[]` operator:

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

W przykładzie użyto [ `stackalloc` operator](stackalloc.md) przydzielić blok pamięci na stosie.

> [!NOTE]
> Operator dostępu do elementu wskaźnik nie sprawdzaj liczbach błędy.

Nie można użyć `[]` wskaźnika elementu dostępu za pomocą wyrażenia typu `void*`.

Możesz również użyć `[]` operator [tablicy dostępu do elementu lub indeksator](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Operatory arytmetyczne wskaźnika

Można wykonywać następujące operacje arytmetyczne ze wskaźnikami:

- Dodaj lub Odejmij wartość całkowitą na lub ze wskaźnika
- Odejmowania dwóch wskaźników
- Inkrementacyjna lub dekrementacyjna wskaźnika

Nie można wykonać te operacje za pomocą wskaźników typu `void*`.

Aby uzyskać informacji na temat obsługiwanych operacji arytmetycznych na wartościach typów liczbowych, zobacz [operatorów arytmetycznych](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Dodawania lub odejmowania liczb całkowitych do lub ze wskaźnika

Dla wskaźnika `p` typu `T*` i wyrażenie `n` niejawnej konwersji typu `int`, `uint`, `long`, lub `ulong`, dodawania i odejmowania są zdefiniowane w następujący sposób:

- Zarówno `p + n` i `n + p` wyrażenia dają wskaźnika typu `T*` , wynikiem dodawania `n * sizeof(T)` adres podany przez `p`.
- `p - n` Wyrażenie powoduje wskaźnika typu `T*` , wynikiem odejmowania `n * sizeof(T)` z adresem podanym przez `p`.

[ `sizeof` Operator](../keywords/sizeof.md) uzyskuje rozmiar typu w bajtach.

W poniższym przykładzie pokazano użycie `+` operator za pomocą wskaźnika:

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odejmowanie wskaźnika

Dla dwóch wskaźników `p1` i `p2` typu `T*`, wyrażenie `p1 - p2` tworzy różnica między adresy podane przez `p1` i `p2` podzielona przez `sizeof(T)`. Typ wyniku jest `long`. Oznacza to, że `p1 - p2` jest obliczana jako `((long)(p1) - (long)(p2)) / sizeof(T)`.

W poniższym przykładzie pokazano odejmowanie wskaźnika:

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Wskaźnik inkrementacja i dekrementacja

`++` Operator inkrementacji [dodaje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do swojego operandu wskaźnika. `--` Operatora dekrementacyjnego [odejmuje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 z argumentem wskaźnika.

Oba operatory są obsługiwane w dwóch formach: przyrostków (`p++` i `p--`) i prefiksu (`++p` i `--p`). Wynik `p++` i `p--` jest wartością `p` *przed* wykonać operację. Wynik `++p` i `--p` jest wartością `p` *po* wykonać operację.

Poniższy przykład pokazuje zachowanie operatory inkrementacji przyrostka i prefiksu:

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operatory porównania wskaźnika

Możesz użyć `==`, `!=`, `<`, `>`, `<=`, i `>=` operatory, aby porównać argumentów operacji typu wskaźnika, w tym `void*`. Te operatory porównują adresy podane przez dwa operandy tak, jakby były one liczb całkowitych bez znaku.

Aby uzyskać informacje o zachowaniu tych operatorów w przypadku argumentów operacji innych typów, zobacz [Operatory równości](equality-operators.md) i [operatory porównania](comparison-operators.md) artykułów.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Następujący wskaźnik zamówienia listy powiązane operatory rozpoczyna się od najwyższy priorytet najniższy:

- Inkrementacja przyrostkowa `x++` i dekrementacyjne `x--` operatorów i `->` i `[]` operatorów
- Inkrementacja przedrostkowa `++x` i dekrementacyjne `--x` operatorów i `&` i `*` operatorów
- Dodatek `+` i `-` operatorów
- Porównanie `<`, `>`, `<=`, i `>=` operatorów
- Równość `==` i `!=` operatorów

Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów.

Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika nie mogą przeciążać wskaźnik związane z operatorów `&`, `*`, `->`, i `[]`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Stałe i ruchome zmiennych](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Operator address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Operatora pośredniego wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Dostęp do elementu członkowskiego wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Dostęp do elementu wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Arytmetyczny wskaźnik](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Wskaźnik inkrementacja i dekrementacja](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Porównanie wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [słowa kluczowego unsafe](../keywords/unsafe.md)
- [Fixed — słowo kluczowe](../keywords/fixed-statement.md)
- [stackalloc — operator](stackalloc.md)
- [sizeof — operator](../keywords/sizeof.md)

---
title: Operatory powiązane z wskaźnikiem — C# odwołanie
description: Dowiedz C# się więcej na temat operatorów, których można używać podczas pracy ze wskaźnikami.
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
ms.openlocfilehash: 9851fcd056eeee33b8f3d7e9d541f9fa43b36d29
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036154"
---
# <a name="pointer-related-operators-c-reference"></a>Operatory powiązane z wskaźnikiem (C# odwołanie)

Można użyć następujących operatorów do pracy ze wskaźnikami:

- Operator jednoargumentowy [`&` (Address-of)](#address-of-operator-) : Aby uzyskać adres zmiennej
- Operator jednoargumentowy [`*` (pośredni wskaźnik)](#pointer-indirection-operator-) : Aby uzyskać zmienną wskazywaną przez wskaźnik
- Operatory [`->` (dostęp do elementów członkowskich)](#pointer-member-access-operator--) i [`[]` (dostęp do elementów)](#pointer-element-access-operator-)
- Operatory arytmetyczne [`+`, `-`, `++`i `--`](#pointer-arithmetic-operators)
- Operatory porównania [`==`, `!=`, `<`, `>`, `<=`i `>=`](#pointer-comparison-operators)

Aby uzyskać informacje na temat typów wskaźnikowych, zobacz [typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Wszystkie operacje ze wskaźnikami wymagają [niebezpiecznego](../keywords/unsafe.md) kontekstu. Kod, który zawiera niebezpieczne bloki, musi być skompilowany przy użyciu opcji kompilatora [`-unsafe`](../compiler-options/unsafe-compiler-option.md) .

## <a name="address-of-operator-"></a>&amp; operatora adresu

Jednoargumentowy operator `&` zwraca adres tego operandu:

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

Argument operacji operatora `&` musi być zmienną stałą. Zmienne *stałe* są zmiennymi, które znajdują się w lokalizacjach magazynu, które nie mają wpływ na działanie [modułu wyrzucania elementów bezużytecznych](../../../standard/garbage-collection/index.md). W poprzednim przykładzie zmienna lokalna `number` to stała zmienna, ponieważ znajduje się ona na stosie. Zmienne, które znajdują się w lokalizacjach magazynu, na które może mieć wpływ Moduł wyrzucania elementów bezużytecznych (na przykład rezlokalizowane), *są nazywane* zmiennymi zmiennych. Pola obiektów i elementy tablicy to przykłady ruchomych zmiennych. Adres ruchomej zmiennej można pobrać, jeśli "Napraw" lub "PIN", za pomocą [instrukcji`fixed`](../keywords/fixed-statement.md). Uzyskany adres jest prawidłowy tylko wewnątrz bloku instrukcji `fixed`. Poniższy przykład pokazuje, jak używać instrukcji `fixed` i operatora `&`:

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Nie można uzyskać adresu stałej ani wartości.

Aby uzyskać więcej informacji na temat zmiennych stałych i przenośnych, zobacz sekcję [zmienne stałe i ruchome](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Operator `&` binarny oblicza wartość [logiczną i](boolean-logical-operators.md#logical-and-operator-) jej operandy logiczne oraz [koniunkcję bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej całkowite argumenty operacji.

## <a name="pointer-indirection-operator-"></a>Operator pośredni wskaźnika *

Operator jednoargumentowy pośredni wskaźnika, `*` uzyskuje zmienną, do której wskazuje operand. Jest on również znany jako operator dereferencji. Argument operacji operatora `*` musi być typu wskaźnika.

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

Nie można zastosować operatora `*` do wyrażenia typu `void*`.

Operator `*` binarny oblicza [iloczyn](arithmetic-operators.md#multiplication-operator-) swoich argumentów liczbowych.

## <a name="pointer-member-access-operator--"></a>Operator dostępu do elementów członkowskich wskaźnika — >

Operator `->` łączy [pośredni wskaźnik](#pointer-indirection-operator-) i [dostęp do elementów członkowskich](member-access-operators.md#member-access-operator-). Oznacza to, że jeśli `x` jest wskaźnikiem typu `T*`, a `y` jest dostępną składową typu `T`, wyrażenie formularza

```csharp
x->y
```

jest równoważny

```csharp
(*x).y
```

Poniższy przykład ilustruje użycie operatora `->`:

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

Nie można zastosować operatora `->` do wyrażenia typu `void*`.

## <a name="pointer-element-access-operator-"></a>Operator dostępu do elementów wskaźnika []

Dla wyrażenia `p` typu wskaźnika, dostęp elementu wskaźnika do formularza `p[n]` jest oceniane jako `*(p + n)`, gdzie `n` musi być typem niejawnie konwertowanym na `int`, `uint`, `long`lub `ulong`. Aby uzyskać informacje o zachowaniu operatora `+` ze wskaźnikami, zobacz [Dodawanie lub odejmowanie wartości całkowitej do lub z sekcji wskaźnika](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .

W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy za pomocą wskaźnika i operatora `[]`:

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

W przykładzie używa [operatora`stackalloc`](stackalloc.md) , aby przydzielić blok pamięci na stosie.

> [!NOTE]
> Operator dostępu do elementów wskaźnika nie sprawdza występowania błędów poza granicami.

Nie można użyć `[]` do uzyskiwania dostępu do elementu wskaźnika przy użyciu wyrażenia typu `void*`.

Można również użyć operatora `[]` dla [elementu tablicy lub dostępu indeksatora](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Operatory arytmetyczne wskaźnika

Za pomocą wskaźników można wykonywać następujące operacje arytmetyczne:

- Dodaj lub Odejmij wartość całkowitą do lub ze wskaźnika
- Odejmij dwa wskaźniki
- Zwiększ lub Zmniejsz wskaźnik

Nie można wykonać tych operacji ze wskaźnikami typu `void*`.

Aby uzyskać informacje o obsługiwanych operacjach arytmetycznych o typach liczbowych, zobacz [Operatory arytmetyczne](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Dodanie lub odjęcie wartości całkowitej do lub ze wskaźnika

Dla wskaźnika `p` typu `T*` i `n` wyrażenia typu niejawnie przekonwertowany na `int`, `uint`, `long`lub `ulong`, Dodawanie i odejmowanie są zdefiniowane w następujący sposób:

- Wyrażenia `p + n` i `n + p` tworzą wskaźnik typu `T*`, który powoduje dodanie `n * sizeof(T)` do adresu podanego przez `p`.
- Wyrażenie `p - n` generuje wskaźnik typu `T*`, który wynika z odejmowania `n * sizeof(T)` od adresu podanych przez `p`.

[Operator`sizeof`](sizeof.md) uzyskuje rozmiar typu w bajtach.

Poniższy przykład ilustruje użycie operatora `+` ze wskaźnikiem:

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odejmowanie wskaźnika

W przypadku dwóch wskaźników `p1` i `p2` typu `T*`wyrażenie `p1 - p2` powoduje różnicę między adresami podaną przez `p1` i `p2` podzieloną przez `sizeof(T)`. Typ wyniku jest `long`. Oznacza to, że `p1 - p2` jest obliczana jako `((long)(p1) - (long)(p2)) / sizeof(T)`.

Poniższy przykład ilustruje odejmowanie wskaźnika:

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Zwiększenie i zmniejszenie wskaźnika

Operator przyrostu `++` [dodaje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do jego operandu wskaźnika. Operator zmniejszania `--` [odejmuje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 od jego operandu wskaźnika.

Oba operatory są obsługiwane w dwóch formach: przyrostki (`p++` i `p--`) oraz prefiks (`++p` i `--p`). Wynik `p++` i `p--` jest wartością `p` *przed* operacją. Wynik `++p` i `--p` jest wartością `p` *po* operacji.

W poniższym przykładzie przedstawiono zachowanie operatorów przyrostu przyrostkowego i powiększania:

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operatory porównania wskaźnika

Operatory `==`, `!=`, `<`, `>`, `<=`i `>=` służą do porównywania operandów dowolnego typu wskaźnika, w tym `void*`. Te operatory porównują adresy podane przez dwa operandy, tak jakby były to liczby całkowite bez znaku.

Aby uzyskać informacje o zachowaniu tych operatorów dla operandów innych typów, zobacz artykuły [Operatory równości](equality-operators.md) i [Operatory porównania](comparison-operators.md) .

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Poniższa lista kolejności pokrewnych operatorów, rozpoczynając od najwyższego priorytetu do najniższego:

- Przyrosty przyrostkowe `x++` i zmniejszają operatory `x--` i operatory `->` i `[]`
- `++x` przyrostu prefiksu i zmniejszaj operatory `--x` i operatory `&` i `*`
- Addytywne `+` i operatory `-`
- Porównanie `<`, `>`, `<=`i operatory `>=`
- Operatory równości `==` i `!=`

Użyj nawiasów `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów.

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [ C# Operators](index.md) .

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika nie może przeciążać operatorów powiązanych ze wskaźnikami `&`, `*`, `->`i `[]`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Zmienne stałe i ruchome](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Operator address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Pośredni wskaźnik](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Dostęp do elementu członkowskiego wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Dostęp do elementu wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Arytmetyka wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Zwiększenie i zmniejszenie wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Porównanie wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [unsafe — słowo kluczowe](../keywords/unsafe.md)
- [FIXED — słowo kluczowe](../keywords/fixed-statement.md)
- [operator stackalloc](stackalloc.md)
- [sizeof — Operator](sizeof.md)

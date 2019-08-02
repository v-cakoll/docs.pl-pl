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
ms.openlocfilehash: 830aef8546191df3df4a70e350ba561367a9e474
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512351"
---
# <a name="pointer-related-operators-c-reference"></a>Operatory powiązane z wskaźnikiem (C# odwołanie)

Można użyć następujących operatorów do pracy ze wskaźnikami:

- Operator jednoargumentowy [ `&` (Address-of)](#address-of-operator-) : Aby uzyskać adres zmiennej
- Operator jednoargumentowy [ `*` (pośredni wskaźnik)](#pointer-indirection-operator-) : Aby uzyskać zmienną wskazywaną przez wskaźnik
- Operatory [(dostęp do elementów członkowskich) i (dostęp do elementów) `->` ](#pointer-member-access-operator--) [ `[]` ](#pointer-element-access-operator-)
- [ Operatory`+`arytmetyczne `-`,, `++`i`--`](#pointer-arithmetic-operators)
- Operatory [ `==`porównania `!=`, ,,`<=`, i `<` `>``>=`](#pointer-comparison-operators)

Aby uzyskać informacje na temat typów wskaźnikowych, zobacz [typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Wszystkie operacje ze wskaźnikami wymagają [](../keywords/unsafe.md) niebezpiecznego kontekstu. Kod, który zawiera niebezpieczne bloki, musi być skompilowany przy [`-unsafe`](../compiler-options/unsafe-compiler-option.md) użyciu opcji kompilatora.

## <a name="address-of-operator-"></a>Operator address-of&amp;

Operator jednoargumentowy `&` zwraca adres tego operandu:

[!code-csharp[address of local](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOf)]

Operand `&` operatora musi być zmienną stałą. Zmienne *stałe* są zmiennymi, które znajdują się w lokalizacjach magazynu, które nie mają wpływ na działanie [modułu wyrzucania elementów](../../../standard/garbage-collection/index.md)bezużytecznych. W poprzednim przykładzie zmienna `number` lokalna to stała zmienna, ponieważ znajduje się ona na stosie. Zmienne, które znajdują się w lokalizacjach magazynu, na które może mieć wpływ Moduł wyrzucania elementów bezużytecznych (na przykład rezlokalizowane), *są nazywane* zmiennymi zmiennych. Pola obiektów i elementy tablicy to przykłady ruchomych zmiennych. Adres ruchomej zmiennej można pobrać, jeśli "Napraw" lub "PIN", za pomocą instrukcji [FIXED](../keywords/fixed-statement.md) . Uzyskany adres jest prawidłowy tylko dla czasu trwania `fixed` bloku instrukcji. Poniższy przykład pokazuje, jak używać `fixed` instrukcji `&` i operatora:

[!code-csharp[address of fixed](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddressOfFixed)]

Nie można uzyskać adresu stałej ani wartości.

Aby uzyskać więcej informacji na temat zmiennych stałych i przenośnych, zobacz sekcję [zmienne stałe i](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) ruchome [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Operator binarny `&` oblicza wartość [logiczną i](boolean-logical-operators.md#logical-and-operator-) jej operandy logiczne oraz koniunkcję bitową [i](bitwise-and-shift-operators.md#logical-and-operator-) jej całkowite argumenty operacji.

## <a name="pointer-indirection-operator-"></a>Operator pośredni wskaźnika *

Operator operatora `*` bezoperatorowego pośredni uzyskuje zmienną, do której odwołuje się argument operacji. Jest on również znany jako operator dereferencji. Operand `*` operatora musi być typu wskaźnika.

[!code-csharp[pointer indirection](~/samples/csharp/language-reference/operators/PointerOperators.cs#PointerIndirection)]

Nie można zastosować `*` operatora do wyrażenia typu `void*`.

Operator binarny `*` oblicza [iloczyn](arithmetic-operators.md#multiplication-operator-) argumentów liczbowych.

## <a name="pointer-member-access-operator--"></a>Operator dostępu do elementów członkowskich wskaźnika — >

Operator łączy [pośredni wskaźnik](#pointer-indirection-operator-) i [dostęp do elementów członkowskich.](member-access-operators.md#member-access-operator-) `->` Oznacza to, że `x` jeśli jest wskaźnikiem typu `T*` i `y` jest dostępnym elementem członkowskim `T`, wyrażenie formularza

```csharp
x->y
```

odpowiada wyrażeniu

```csharp
(*x).y
```

Poniższy przykład ilustruje użycie `->` operatora:

[!code-csharp[pointer member access](~/samples/csharp/language-reference/operators/PointerOperators.cs#MemberAccess)]

Nie można zastosować `->` operatora do wyrażenia typu `void*`.

## <a name="pointer-element-access-operator-"></a>Operator dostępu do elementów wskaźnika []

Dla `p` wyrażenia `long`typu wskaźnika dostęp do `p[n]` elementu wskaźnika jest oceniany jako `*(p + n)`, gdzie `n` musi być typem niejawnie konwertowanym na `int`, `uint`,, lub `ulong`. Aby uzyskać informacje o zachowaniu `+` operatora ze wskaźnikami, zobacz [Dodawanie lub odejmowanie wartości całkowitej do lub z sekcji wskaźnika](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) .

W poniższym przykładzie pokazano, jak uzyskać dostęp do elementów tablicy za pomocą wskaźnika `[]` i operatora:

[!code-csharp[pointer element access](~/samples/csharp/language-reference/operators/PointerOperators.cs#ElementAccess)]

W przykładzie używa [ `stackalloc` operatora](stackalloc.md) , aby przydzielić blok pamięci na stosie.

> [!NOTE]
> Operator dostępu do elementów wskaźnika nie sprawdza występowania błędów poza granicami.

Nie można użyć `[]` do uzyskania dostępu do elementu wskaźnika z wyrażeniem `void*`typu.

Można też użyć `[]` operatora dla [elementu tablicy lub dostępu indeksatora](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Operatory arytmetyczne wskaźnika

Za pomocą wskaźników można wykonywać następujące operacje arytmetyczne:

- Dodaj lub Odejmij wartość całkowitą do lub ze wskaźnika
- Odejmij dwa wskaźniki
- Zwiększ lub Zmniejsz wskaźnik

Nie można wykonać tych operacji ze wskaźnikami typu `void*`.

Aby uzyskać informacje o obsługiwanych operacjach arytmetycznych o typach liczbowych, zobacz [Operatory arytmetyczne](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Dodanie lub odjęcie wartości całkowitej do lub ze wskaźnika

Dla `p` wskaźnika `ulong`typu `uint` `long`i wyrażenia `n` typu niejawnie konwertowany na `int`,,, lub, Dodawanie i odejmowanie są zdefiniowane w następujący sposób: `T*`

- Oba `p + n` `T*` i `n + p` wyrażenia tworzą wskaźnik typu, który wynika z dodania `n * sizeof(T)` do adresu podanego przez `p`.
- Wyrażenie generuje wskaźnik typu `T*` `p`, który wynika z odejmowania odadresupodanychprzez.`n * sizeof(T)` `p - n`

Operator uzyskuje rozmiar typu w bajtach. [ `sizeof` ](sizeof.md)

Poniższy przykład ilustruje użycie `+` operatora ze wskaźnikiem:

[!code-csharp[pointer addition](~/samples/csharp/language-reference/operators/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odejmowanie wskaźnika

W przypadku dwóch `p1` wskaźników `p2` i typu `T*`wyrażenie `p1 - p2` tworzy różnicę między adresami podaną przez `p1` i `p2` podzieloną przez `sizeof(T)`. Typ wyniku to `long`. Oznacza to, `p1 - p2` że jest obliczana `((long)(p1) - (long)(p2)) / sizeof(T)`jako.

Poniższy przykład ilustruje odejmowanie wskaźnika:

[!code-csharp[pointer subtraction](~/samples/csharp/language-reference/operators/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Zwiększenie i zmniejszenie wskaźnika

Operator przyrostu dodaje 1 do jego operandu wskaźnika. [](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) `++` Operator zmniejszania odejmuje 1 od jego operandu wskaźnika. [](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) `--`

Oba operatory są obsługiwane w dwóch formach: przyrostka `p--`(`p++` i) oraz`++p` prefiks `--p`(i). Wynik `p++` i `p--` jest wartością `p` *przed* operacją. Wynik `++p` i `--p` jest wartością `p` *po* operacji.

W poniższym przykładzie przedstawiono zachowanie operatorów przyrostu przyrostkowego i powiększania:

[!code-csharp[pointer increment](~/samples/csharp/language-reference/operators/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operatory porównania wskaźnika

`==`Operatory `void*`, `!=`, ,`<` ,i`>=` służą do porównywania operandów dowolnego typu wskaźnika, w tym. `>` `<=` Te operatory porównują adresy podane przez dwa operandy, tak jakby były to liczby całkowite bez znaku.

Aby uzyskać informacje o zachowaniu tych operatorów dla operandów innych typów, zobacz artykuły [Operatory równości](equality-operators.md) i [Operatory porównania](comparison-operators.md) .

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Poniższa lista kolejności pokrewnych operatorów, rozpoczynając od najwyższego priorytetu do najniższego:

- Operatory `x++` `x--` przyrostka`[]` i zmniejszanie przyrostkowe oraz operatory i `->`
- Operatory `++x` `--x` przyrostu`*` i zmniejszania prefiksu oraz operatory i `&`
- Dodatek `+` i `-` operatory
- Porównanie `<`, `>`, i`<=`operatory `>=`
- Równość `==` i `!=` operatory

Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów.

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](index.md).

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika nie `&`może przeciążać operatorów `*`powiązanych ze wskaźnikiem, `[]`, `->`i.

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

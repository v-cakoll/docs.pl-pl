---
title: Operatory powiązane z wskaźnikiem — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, których można używać podczas pracy ze wskaźnikami.
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
ms.openlocfilehash: 7c95fe07220a78b388a5c6850e4123feb029d951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399547"
---
# <a name="pointer-related-operators-c-reference"></a>Operatory powiązane ze wskaźnikiem (odwołanie do języka C#)

Do pracy ze wskaźnikami można używać następujących operatorów:

- Operator unary [ `&` (address-of):](#address-of-operator-) aby uzyskać adres zmiennej
- Operator jednoargumentowy [ `*` (pośredni wskaźnik):](#pointer-indirection-operator-) aby uzyskać zmienną wskazywaną przez wskaźnik
- [ `->` Operatorzy (dostęp do elementów członkowskich)](#pointer-member-access-operator--) i [ `[]` (dostęp do elementów)](#pointer-element-access-operator-)
- Operatory [ `+` `-`arytmetyczne `++`, , i`--`](#pointer-arithmetic-operators)
- Operatorzy [ `==` `!=` `<`porównania `>` `<=`, , , i`>=`](#pointer-comparison-operators)

Aby uzyskać informacje o typach wskaźników, zobacz [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Każda operacja ze wskaźnikami wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu. Kod, który zawiera niebezpieczne bloki [`-unsafe`](../compiler-options/unsafe-compiler-option.md) muszą być skompilowane z opcją kompilatora.

## <a name="address-of-operator-"></a>Operator adresowy&amp;

Operator nieurodzajny `&` zwraca adres swojego operandu:

[!code-csharp[address of local](snippets/PointerOperators.cs#AddressOf)]

Operand `&` operatora musi być zmienną stałą. *Zmienne stałe* są zmienne, które znajdują się w miejscach magazynowania, które nie mają wpływu na działanie [modułu odśmiecania pamięci](../../../standard/garbage-collection/index.md). W poprzednim przykładzie zmienna `number` lokalna jest zmienną stałą, ponieważ znajduje się na stosie. Zmienne znajdujące się w lokalizacjach magazynu, na które może mieć wpływ moduł odśmiecania pamięci (na przykład przeniesiony) są nazywane zmiennymi *ruchomymi.* Pola obiektów i elementy tablicy są przykładami zmiennych ruchomych. Możesz uzyskać adres ruchomej zmiennej, jeśli "naprawisz" lub "pin", z [ `fixed` oświadczeniem](../keywords/fixed-statement.md). Otrzymany adres jest prawidłowy tylko `fixed` wewnątrz bloku instrukcji. W poniższym przykładzie pokazano, `fixed` `&` jak używać instrukcji i operatora:

[!code-csharp[address of fixed](snippets/PointerOperators.cs#AddressOfFixed)]

Nie można uzyskać adresu stałej lub wartości.

Aby uzyskać więcej informacji na temat zmiennych stałych i ruchomych, zobacz [stałe i ruchome zmienne](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

Operator `&` binarny oblicza [logiczne i jego](boolean-logical-operators.md#logical-and-operator-) operands boolean lub [bitwise logiczne i](bitwise-and-shift-operators.md#logical-and-operator-) jego integralną operands.

## <a name="pointer-indirection-operator-"></a>Operator pośredni wskaźnika *

Operator `*` pośredni wskaźnika jednoargumentowego uzyskuje zmienną, do której wskazuje jego operand. Jest również znany jako operator wyłusk. Operand `*` operatora musi być typu wskaźnika.

[!code-csharp[pointer indirection](snippets/PointerOperators.cs#PointerIndirection)]

Nie można `*` zastosować operatora do `void*`wyrażenia typu .

Operator `*` binarny oblicza [iloczyn](arithmetic-operators.md#multiplication-operator-) swoich operacji numerycznych.

## <a name="pointer-member-access-operator--"></a>Operator dostępu do elementu członkowskiego wskaźnika ->

Operator `->` łączy [wskaźnik pośredni](#pointer-indirection-operator-) i [dostęp do elementu członkowskiego](member-access-operators.md#member-access-operator-). Oznacza to, `x` że jeśli `T*` jest `y` wskaźnikiem typu `T`i jest dostępnym elementem członkowskim typu , wyrażenie monin

```csharp
x->y
```

jest równoważny

```csharp
(*x).y
```

W poniższym przykładzie przedstawiono `->` użycie operatora:

[!code-csharp[pointer member access](snippets/PointerOperators.cs#MemberAccess)]

Nie można `->` zastosować operatora do `void*`wyrażenia typu .

## <a name="pointer-element-access-operator-"></a>Operator dostępu do elementu wskaźnika []

Dla wyrażenia `p` typu wskaźnika dostęp elementu wskaźnika `p[n]` formularza jest `*(p + n)` `n` obliczany jako , gdzie musi `int`być `uint` `long`typu `ulong`niejawnie cabrio do , , , lub . Aby uzyskać informacje na `+` temat zachowania operatora ze wskaźnikami, zobacz [Dodawanie lub odejmowanie wartości integralnej do lub z sekcji wskaźnika.](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)

W poniższym przykładzie pokazano, jak uzyskać `[]` dostęp do elementów tablicy ze wskaźnikiem i operatorem:

[!code-csharp[pointer element access](snippets/PointerOperators.cs#ElementAccess)]

W przykładzie [ `stackalloc` ](stackalloc.md) użyto operatora do przydzielenia bloku pamięci na stosie.

> [!NOTE]
> Operator dostępu do elementu wskaźnika nie sprawdza błędów poza granicami.

Nie można `[]` użyć dostępu do elementu `void*`wskaźnika z wyrażeniem typu .

Można również użyć `[]` operatora dla [dostępu do elementu tablicy lub indeksatora](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Operatory arytmetyczne wskaźnika

Za pomocą wskaźników można wykonywać następujące operacje arytmetyczne:

- Dodawanie lub odejmowanie wartości integralnej do lub ze wskaźnika
- Odejmowanie dwóch wskaźników
- Zwiększanie lub zmniejszanie wskaźnika

Nie można wykonać tych operacji `void*`ze wskaźnikami typu .

Aby uzyskać informacje o obsługiwanych operacjach arytmetycznych z typami liczbowymi, zobacz [Operatory arytmetyczne](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Dodawanie lub odejmowanie wartości integralnej do lub ze wskaźnika

`p` Dla wskaźnika `T*` typu i `n` wyrażenia typu niejawnie `int` `uint`konwertowalne na , , `long`lub `ulong`, dodawanie i odejmowanie są zdefiniowane w następujący sposób:

- Oba `p + n` `n + p` i wyrażenia dają wskaźnik `T*` typu, `n * sizeof(T)` który wynika z `p`dodawania do adresu podane przez .
- Wyrażenie `p - n` generuje wskaźnik typu, `T*` który wynika z `n * sizeof(T)` odjęcia `p`od adresu podane przez .

[ `sizeof` Operator](sizeof.md) uzyskuje rozmiar typu w bajtach.

W poniższym przykładzie przedstawiono `+` użycie operatora ze wskaźnikiem:

[!code-csharp[pointer addition](snippets/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odejmowanie wskaźnika

Dla dwóch `p1` wskaźników `p2` i `T*`typu `p1 - p2` wyrażenie tworzy różnicę między adresami podanymi przez `p1` i `p2` podzielonymi przez `sizeof(T)`. Typem wyniku jest `long`. Oznacza to, `p1 - p2` że `((long)(p1) - (long)(p2)) / sizeof(T)`jest obliczana jako .

W poniższym przykładzie przedstawiono odejmowanie wskaźnika:

[!code-csharp[pointer subtraction](snippets/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Przyrost wskaźnika i zmniejszanie

Operator `++` przyrostu [dodaje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do swojego operandu wskaźnika. Operator `--` zmniejszania [odejmuje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 od swojego operandu wskaźnika.

Oba operatory są obsługiwane w dwóch`p++` `p--`formach: postfix ( i ) i prefiks (`++p` i `--p`). Wynik `p++` i `p--` jest wartością `p` *przed* operacją. Wynik `++p` i `--p` jest wartością `p` *po* operacji.

W poniższym przykładzie przedstawiono zachowanie zarówno operatorów przyrostu postfix i prefiksu:

[!code-csharp[pointer increment](snippets/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operatory porównania wskaźników

Za pomocą `==`operacji `!=` `<` `>` `<=` `>=` można porównywać operandy dowolnego typu wskaźnika, `void*`w tym . Operatorzy ci porównują adresy podane przez dwa argumenty tak, jakby były liczbami całkowitymi bez znaku.

Aby uzyskać informacje na temat zachowania tych operatorów dla operandów innych typów, zobacz [Operatory równości](equality-operators.md) i [porównywania operatorów artykułów.](comparison-operators.md)

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Następująca lista zleca operatory powiązane ze wskaźnikiem, zaczynając od najwyższego pierwszeństwa do najniższego:

- Operatory `x++` przyrostkowe i `x--` zmniejszania `->` `[]` oraz operatorzy i operatorzy
- Operatory przyrostu `++x` i zmniejszania `--x` prefiksów oraz operatorzy `&` i `*` operatorzy
- `+` Dodatki `-` i podmioty gospodarcze
- Porównanie `<` `>`, `<=`i `>=` operatorzy
- `==` Równość `!=` i operatorzy

Użyj nawiasów, `()`, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora.

Aby uzyskać pełną listę operatorów Języka C# uporządkowane według poziomu pierwszeństwa, zobacz [pierwszeństwo operatora](index.md#operator-precedence) sekcji [operatorów C#artykułu.](index.md)

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika nie może `&` `*`przeciążyć operatorów związanych ze wskaźnikiem , , `->`i `[]`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Zmienne stałe i ruchome](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Operator adresowy](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Wskaźnik pośredni](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Dostęp do elementu członkowskiego wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Dostęp do elementu wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Arytmetyczny wskaźnik](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Przyrost wskaźnika i zmniejszanie](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Porównanie wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [niebezpieczne słowo kluczowe](../keywords/unsafe.md)
- [stałe słowo kluczowe](../keywords/fixed-statement.md)
- [stackalloc, operator](stackalloc.md)
- [sizeof, operator](sizeof.md)

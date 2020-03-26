---
title: Operatory powiązane ze wskaźnikiem — odwołanie do języka C#
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
ms.openlocfilehash: fd25cd419f8c3bfe905850e6a252f4a8cf65478c
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507103"
---
# <a name="pointer-related-operators-c-reference"></a>Operatory powiązane ze wskaźnikiem (odwołanie do języka C#)

Do pracy ze wskaźnikami można używać następujących operatorów:

- Operator [ `&` dwuaryjny (adres:](#address-of-operator-) aby uzyskać adres zmiennej
- Operator unary [ `*` (pośredni wskaźnik):](#pointer-indirection-operator-) aby uzyskać zmienną wskazywana przez wskaźnik
- Operatory [ `->` (dostęp do elementów członkowskich)](#pointer-member-access-operator--) i [ `[]` (dostęp do elementów)](#pointer-element-access-operator-)
- Operatory [ `+` `-`arytmetyczne `++`, , i`--`](#pointer-arithmetic-operators)
- Operatory [ `==` `!=`porównawcze `>` `<=`, `<`, , , i`>=`](#pointer-comparison-operators)

Aby uzyskać informacje o typach wskaźników, zobacz [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Każda operacja ze wskaźnikami wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu. Kod, który zawiera niebezpieczne bloki muszą [`-unsafe`](../compiler-options/unsafe-compiler-option.md) być skompilowane z opcją kompilatora.

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a>Adres operatora&amp;

Operator unary `&` zwraca adres swojego operandu:

[!code-csharp[address of local](snippets/PointerOperators.cs#AddressOf)]

Operand `&` operatora musi być zmienną stałą. *Stałe* zmienne to zmienne, które znajdują się w lokalizacjach magazynu, na które nie ma wpływu działanie modułu zbierającego [elementy bezużyteczne.](../../../standard/garbage-collection/index.md) W poprzednim przykładzie zmienna `number` lokalna jest zmienną stałą, ponieważ znajduje się na stosie. Zmienne, które znajdują się w lokalizacjach magazynu, które mogą mieć wpływ na moduł zbierający elementy bezużyteczne (na przykład przeniesiony) są *nazywane* zmiennymi ruchomymi. Pola obiektów i elementy tablicy są przykładami zmiennych ruchomych. Możesz uzyskać adres zmiennej ruchomej, jeśli "naprawić" lub "przypiąć", to z [ `fixed` instrukcją](../keywords/fixed-statement.md). Uzyskany adres jest prawidłowy tylko `fixed` wewnątrz bloku instrukcji. W poniższym `fixed` przykładzie pokazano, `&` jak używać instrukcji i operatora:

[!code-csharp[address of fixed](snippets/PointerOperators.cs#AddressOfFixed)]

Nie można uzyskać adresu stałej lub wartości.

Aby uzyskać więcej informacji na temat zmiennych stałych i ruchomych, zobacz sekcję [Stałe i ruchome zmienne](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

Operator `&` binarny oblicza [logiczne i](boolean-logical-operators.md#logical-and-operator-) jego boolean operands lub [bitowe logiczne i](bitwise-and-shift-operators.md#logical-and-operator-) jego integralną operands.

## <a name="pointer-indirection-operator-"></a>Operator pośredni wskaźnik *

Operator pośredni wskaźnika `*` ujednawczy uzyskuje zmienną, do której wskazuje jego operand. Jest również znany jako operator dereference. Operand `*` operatora musi być typu wskaźnika.

[!code-csharp[pointer indirection](snippets/PointerOperators.cs#PointerIndirection)]

Nie można `*` zastosować operatora do `void*`wyrażenia typu .

Operator `*` binarny oblicza [iloczyn](arithmetic-operators.md#multiplication-operator-) jego argumentów liczbowych.

## <a name="pointer-member-access-operator--"></a>Operator dostępu do elementu członkowskiego wskaźnika ->

Operator `->` łączy [pośredni wskaźnik](#pointer-indirection-operator-) i [dostęp do elementu członkowskiego](member-access-operators.md#member-access-expression-). Oznacza to, `x` że jeśli `T*` jest `y` wskaźnikiem typu `T`i jest dostępnym elementem członkowskim typu, wyrażenie formularza

```csharp
x->y
```

jest równoważny

```csharp
(*x).y
```

Poniższy przykład pokazuje użycie `->` operatora:

[!code-csharp[pointer member access](snippets/PointerOperators.cs#MemberAccess)]

Nie można `->` zastosować operatora do `void*`wyrażenia typu .

## <a name="pointer-element-access-operator-"></a>Operator dostępu do elementu wskaźnika []

W przypadku `p` wyrażenia typu wskaźnika dostęp do `p[n]` elementu wskaźnika formularza jest oceniany jako `*(p + n)`, `int`gdzie `long` `n` musi `ulong`być typu niejawnie konwertowane na , `uint`, lub . Aby uzyskać informacje na `+` temat zachowania operatora ze wskaźnikami, zobacz [Dodawanie lub odejmowanie wartości integralnej do lub z sekcji wskaźnika.](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer)

W poniższym przykładzie pokazano, jak uzyskać `[]` dostęp do elementów tablicy za pomocą wskaźnika i operatora:

[!code-csharp[pointer element access](snippets/PointerOperators.cs#ElementAccess)]

W poprzednim przykładzie [ `stackalloc` wyrażenie](stackalloc.md) przydziela blok pamięci na stosie.

> [!NOTE]
> Operator dostępu do elementu wskaźnika nie sprawdza błędów poza granicami.

Nie można `[]` używać dostępu do elementu `void*`wskaźnika z wyrażeniem typu .

Można również użyć `[]` operatora dla [elementu tablicy lub dostępu do indeksatora](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Operatory arytmetyczne wskaźnika

Za pomocą wskaźników można wykonywać następujące operacje arytmetyczne:

- Dodawanie lub odejmowanie wartości integralnej do lub ze wskaźnika
- Odejmij dwa wskaźniki
- Zwiększanie lub zmniejszanie wskaźnika

Nie można wykonywać tych operacji `void*`ze wskaźnikami typu .

Aby uzyskać informacje na temat obsługiwanych operacji arytmetycznych z typami liczbowymi, zobacz [Operatory arytmetyczne](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Dodawanie lub odejmowanie wartości integralnej do lub ze wskaźnika

Dla wskaźnika `p` `T*` typu i `n` wyrażenia typu niejawnie `int` `uint`konwertowane na , `long`, lub `ulong`, dodawanie i odejmowanie są zdefiniowane w następujący sposób:

- Zarówno `p + n` `n + p` wyrażenia, jak i `T*` wyrażenia dają `n * sizeof(T)` wskaźnik typu, `p`który wynika z dodania do adresu podanego przez program .
- Wyrażenie `p - n` tworzy wskaźnik typu, `T*` który wynika z `n * sizeof(T)` odejmowania `p`od adresu podanego przez .

[ `sizeof` Operator](sizeof.md) uzyskuje rozmiar typu w bajtach.

Poniższy przykład pokazuje użycie `+` operatora ze wskaźnikiem:

[!code-csharp[pointer addition](snippets/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Odejmowanie wskaźnika

Dla dwóch `p1` wskaźników `p2` i `T*`typu `p1 - p2` wyrażenie tworzy różnicę między adresami `p2` podanymi `sizeof(T)`przez `p1` i podzielonymi przez . Typem wyniku jest `long`. Oznacza to, `p1 - p2` że `((long)(p1) - (long)(p2)) / sizeof(T)`jest obliczany jako .

W poniższym przykładzie pokazano odejmowanie wskaźnika:

[!code-csharp[pointer subtraction](snippets/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Zwiększanie i zmniejszanie wskaźnika

Operator `++` przyrostu [dodaje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 do jego operand wskaźnika. Operator `--` dekrementacji [odejmuje](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 od jego operand wskaźnika.

Oba operatory są obsługiwane w dwóch`p++` `p--`formach: postfix ( i ) i prefiks (`++p` i `--p`). Wynik `p++` i `p--` jest wartością `p` *przed* operacją. Wynik `++p` i `--p` jest wartością `p` *po* operacji.

Poniższy przykład pokazuje zachowanie operatorów przyrostu postfix i prefiksu:

[!code-csharp[pointer increment](snippets/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Operatory porównania wskaźników

`==`Operatory można `!=`użyć `<` `>`, `<=`, `>=` , i operatorów, aby porównać argumenty dowolnego typu wskaźnika, w tym `void*`. Operatorzy ci porównują adresy podane przez dwa argumenty tak, jakby były niepodpisanymi liczbami całkowitymi.

Aby uzyskać informacje na temat zachowania tych operatorów dla operandów innych typów, zobacz [równości operatorów](equality-operators.md) i [porównania operatorów](comparison-operators.md) artykułów.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Następująca lista porządkuuje operatorów powiązanych wskaźnik, począwszy od najwyższego pierwszeństwa do najniższego:

- Operatory przyrostu `x++` i `x--` dekrementacji `->` `[]` poprawek oraz operatorzy i operatorzy
- Operatory przyrostu `++x` i `--x` dekrementacji `&` `*` prefiksów oraz operatory i operatory
- Dodatki `+` `-` i podmioty gospodarcze
- Porównanie `<` `>`, `<=`, `>=` i operatorów
- `==` Równość `!=` i operatorzy

Użyj nawiasów, `()`aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora.

Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu [pierwszeństwa, zobacz sekcję pierwszeństwo operatora](index.md#operator-precedence) w artykule [Operatory języka C#.](index.md)

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika nie może `&` `*`przeciążać operatorów powiązanych ze wskaźnikiem , `->`i `[]`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Stałe i ruchome zmienne](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Adres operatora](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Pośredni wskaźnik](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Dostęp do elementu członkowskiego wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Dostęp do elementu wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Arytmetyczny wskaźnik](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Zwiększanie i zmniejszanie wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Porównanie wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [niebezpieczne słowo kluczowe](../keywords/unsafe.md)
- [stałe słowo kluczowe](../keywords/fixed-statement.md)
- [stackalloc](stackalloc.md)
- [sizeof, operator](sizeof.md)

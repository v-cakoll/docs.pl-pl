---
title: stała instrukcja - Odwołanie do języka C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 53bee82bf24a847b0b21ed2375d09a6303d4fe48
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507194"
---
# <a name="fixed-statement-c-reference"></a>fixed — Instrukcja (odwołanie w C#)

Instrukcja `fixed` uniemożliwia moduł zbierający elementy bezużyteczne przeniesienie zmiennej ruchomej. Instrukcja `fixed` jest dozwolona tylko w [niebezpiecznym](unsafe.md) kontekście. Za pomocą słowa `fixed` kluczowego można również utworzyć [bufory o stałym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

Instrukcja `fixed` ustawia wskaźnik do zmiennej zarządzanej i "pins" tej zmiennej podczas wykonywania instrukcji. Wskaźniki do ruchomych zmiennych zarządzanych są `fixed` przydatne tylko w kontekście. Bez `fixed` kontekstu wyrzucania elementów bezużytecznych można przenieść zmienne nieprzewidywalnie. Kompilator języka C# umożliwia przypisanie wskaźnika `fixed` do zmiennej zarządzanej w instrukcji.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Wskaźnik można zainicjować przy użyciu tablicy, ciągu, buforu o stałym rozmiarze lub adresu zmiennej. Poniższy przykład ilustruje użycie adresów zmiennych, tablic i ciągów:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Począwszy od języka C# 7.3, `fixed` instrukcja działa na dodatkowe typy poza tablice, ciągi, bufory o stałym rozmiarze lub zmienne niezarządzane. Każdy typ, który implementuje metodę o nazwie `GetPinnableReference` można przypiąć. Musi `GetPinnableReference` zwrócić `ref` zmienną [typu niezarządzanego](../builtin-types/unmanaged-types.md). Typy <xref:System.Span%601?displayProperty=nameWithType> .NET <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> i wprowadzone w .NET Core 2.0 korzystają z tego wzorca i mogą być przypięte. Jest to pokazane w poniższym przykładzie:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Jeśli tworzysz typy, które powinny uczestniczyć <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> w tym wzorzec, zobacz na przykład implementacji wzorca.

Wiele wskaźników można zainicjować w jednej instrukcji, jeśli wszystkie są tego samego typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Aby zainicjować wskaźniki różnych typów, `fixed` po prostu zagnieżdżanie instrukcji, jak pokazano w poniższym przykładzie.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po wykonaniu kodu w instrukcji, wszystkie przypięte zmienne są odpinane i podlegają wyrzucaniu elementów bezużytecznych. W związku z tym nie wskazują `fixed` na te zmienne poza instrukcją. Zmienne zadeklarowane `fixed` w instrukcji są ograniczone do tej instrukcji, co ułatwia:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Wskaźniki zainicjowane `fixed` w instrukcjach są odczytywane tylko zmienne. Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować tę. Zmiennej zadeklarowanej `fixed` w instrukcji nie można zmodyfikować:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Można przydzielić pamięć na stosie, gdzie nie podlega wyrzucania elementów bezużytecznych i dlatego nie musi być przypięty. Aby to zrobić, należy użyć [ `stackalloc` wyrażenia](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz Stała sekcja [instrukcji](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) [specyfikacji języka języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [C# Przewodnik programowania](../../programming-guide/index.md)
- [C# Słowa kluczowe](index.md)
- [unsafe](unsafe.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bufory o stałym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

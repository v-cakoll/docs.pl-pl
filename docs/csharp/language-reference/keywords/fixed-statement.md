---
title: stała instrukcja - Odwołanie do języka C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713521"
---
# <a name="fixed-statement-c-reference"></a>fixed — Instrukcja (odwołanie w C#)

Instrukcja `fixed` uniemożliwia modułowi odśmiecania pamięci przemieszczanie ruchomej zmiennej. Instrukcja `fixed` jest dozwolona tylko w [niebezpiecznym](unsafe.md) kontekście. Za pomocą słowa `fixed` kluczowego można również utworzyć [bufory o stałym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

Instrukcja `fixed` ustawia wskaźnik do zmiennej zarządzanej i "pins", że zmienna podczas wykonywania instrukcji. Wskaźniki do ruchomych zmiennych zarządzanych `fixed` są przydatne tylko w kontekście. Bez `fixed` kontekstu wyrzucania elementów bezużytecznych można przenieść zmienne nieprzewidywalne. Kompilator Języka C# umożliwia tylko przypisanie wskaźnika do zmiennej zarządzanej `fixed` w instrukcji.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Wskaźnik można zainicjować za pomocą tablicy, ciągu, buforu o stałym rozmiarze lub adresu zmiennej. Poniższy przykład ilustruje użycie zmiennych adresów, tablic i ciągów:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Począwszy od Języka C# `fixed` 7.3, instrukcja działa na dodatkowe typy poza tablice, ciągi, bufory o stałym rozmiarze lub zmiennych niezarządzanych. Każdy typ, który implementuje metodę o nazwie `GetPinnableReference` można przypiąć. Musi `GetPinnableReference` zwrócić `ref` zmienną [typu niezarządzanego](../builtin-types/unmanaged-types.md). Typy <xref:System.Span%601?displayProperty=nameWithType> .NET <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> i wprowadzone w .NET Core 2.0 korzystają z tego wzorca i mogą być przypięte. Jest to pokazane w poniższym przykładzie:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Jeśli tworzysz typy, które powinny <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> uczestniczyć w tym wzorzec, zobacz przykład implementowania wzorca.

Wiele wskaźników można zainicjować w jednej instrukcji, jeśli wszystkie są tego samego typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Aby zainicjować wskaźniki różnych typów, `fixed` wystarczy zagnieździć instrukcje, jak pokazano w poniższym przykładzie.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są odpięte i podlegają wyrzucaniu elementów bezużytecznych. W związku z tym nie wskazują `fixed` na te zmienne poza instrukcją. Zmienne zadeklarowane w `fixed` instrukcji są ograniczone do tej instrukcji, co ułatwia:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Wskaźniki zainicjowane `fixed` w instrukcjach są zmiennymi tylko do odczytu. Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować ją. Nie można zmodyfikować zmiennej zadeklarowanej w `fixed` instrukcji:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Można przydzielić pamięć na stosie, gdzie nie podlega wyrzucania elementów bezużytecznych i dlatego nie musi być przypięty. Aby to zrobić, należy użyć [ `stackalloc` operatora](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcja [instrukcja stała](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) [specyfikacji języka Języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [unsafe](unsafe.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bufory o stałym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

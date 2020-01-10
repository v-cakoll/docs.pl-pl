---
title: FIXED — C# odwołanie
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713521"
---
# <a name="fixed-statement-c-reference"></a>fixed — Instrukcja (odwołanie w C#)

Instrukcja `fixed` uniemożliwia ponowne lokalizowanie ruchomej zmiennej przez moduł wyrzucania elementów bezużytecznych. Instrukcja jest dozwolona tylko w niebezpiecznym kontekście. [niebezpieczny](unsafe.md) `fixed` Można również użyć słowa kluczowego `fixed`, aby utworzyć [bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

Instrukcja `fixed` ustawia wskaźnik do zmiennej zarządzanej i "pinezki", która jest zmienna podczas wykonywania instrukcji. Wskaźniki do ruchomych zmiennych zarządzanych są przydatne tylko w kontekście `fixed`. Bez kontekstu `fixed`, wyrzucanie elementów bezużytecznych może przewidzieć nieprzewidywalne zmienne. C# Kompilator umożliwia tylko przypisanie wskaźnika do zmiennej zarządzanej w instrukcji `fixed`.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Wskaźnik można zainicjować za pomocą tablicy, ciągu, buforu o ustalonym rozmiarze lub adresu zmiennej. Poniższy przykład ilustruje użycie adresów zmiennych, tablic i ciągów:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Począwszy od C# 7,3, instrukcja `fixed` działa na dodatkowych typach poza tablicami, ciągami, buforami o ustalonym rozmiarze lub zmiennymi niezarządzanymi. Dowolny typ implementujący metodę o nazwie `GetPinnableReference` może być przypięty. Musi zwracać zmienną typu niezarządzanego. [Cómo se pronuncia
typ niezarządzany](../builtin-types/unmanaged-types.md) `GetPinnableReference` `ref` Typy .NET <xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> wprowadzone w środowisku .NET Core 2,0 używają tego wzorca i mogą być przypięte. Jest to pokazane w poniższym przykładzie:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Jeśli tworzysz typy, które powinny wchodzić w skład tego wzorca, zobacz <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType>, aby zapoznać się z przykładem implementacji wzorca.

W jednej instrukcji można zainicjować wiele wskaźników, jeśli są one tego samego typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Aby zainicjować wskaźniki różnych typów, należy po prostu zagnieździć instrukcje `fixed`, jak pokazano w poniższym przykładzie.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są odpięte i podlegają wyrzucaniu elementów bezużytecznych. W związku z tym nie należy wskazywać na te zmienne poza instrukcją `fixed`. Zmienne zadeklarowane w instrukcji `fixed` są zakresem tej instrukcji, ułatwiając to:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Wskaźniki inicjowane w instrukcjach `fixed` są zmiennymi tylko do odczytu. Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować ją. Zmienna zadeklarowana w instrukcji `fixed` nie może być modyfikowana:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Możesz przydzielić pamięć na stosie, gdzie nie podlega wyrzucaniu elementów bezużytecznych i dlatego nie musi być przypięty. Aby to zrobić, użyj [operatora`stackalloc`](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [FIXED Statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [unsafe](unsafe.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

---
title: FIXED — odwołanie do języka C#
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: d743daca2fa779e300c7e8ab430b1ffff10b434c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401917"
---
# <a name="fixed-statement-c-reference"></a>fixed — Instrukcja (odwołanie w C#)

`fixed`Instrukcja zapobiega ponownemu lokalizowaniu ruchomej zmiennej przez moduł wyrzucania elementów bezużytecznych. `fixed`Instrukcja jest dozwolona tylko w [niebezpiecznym](unsafe.md) kontekście. Możesz również użyć `fixed` słowa kluczowego, aby utworzyć [bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed`Instrukcja ustawia wskaźnik na zmienną zarządzaną i "pinezki", która jest zmienna podczas wykonywania instrukcji. Wskaźniki do ruchomych zmiennych zarządzanych są przydatne tylko w `fixed` kontekście. Bez `fixed` kontekstu, wyrzucanie elementów bezużytecznych może przewidzieć nieprzewidywalne zmienne. Kompilator języka C# umożliwia przypisanie wskaźnika do zmiennej zarządzanej w `fixed` instrukcji.

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

Wskaźnik można zainicjować za pomocą tablicy, ciągu, buforu o ustalonym rozmiarze lub adresu zmiennej. Poniższy przykład ilustruje użycie adresów zmiennych, tablic i ciągów:

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

Począwszy od języka C# 7,3, `fixed` instrukcja działa na dodatkowych typach poza tablicami, ciągami, buforami o ustalonym rozmiarze lub zmiennymi niezarządzanymi. Każdy typ, który implementuje metodę o nazwie, `GetPinnableReference` może być przypięty. `GetPinnableReference`Musi zwracać `ref` zmienną [typu niezarządzanego](../builtin-types/unmanaged-types.md). Typy .NET <xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> wprowadzone w środowisku .net Core 2,0 używają tego wzorca i mogą być przypięte. Pokazano to w następującym przykładzie:

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

Jeśli tworzysz typy, które powinny wchodzić w skład tego wzorca, zobacz, aby zapoznać się <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> z przykładem implementacji wzorca.

W jednej instrukcji można zainicjować wiele wskaźników, jeśli są one tego samego typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Aby zainicjować wskaźniki różnych typów, należy po prostu zagnieżdżać `fixed` instrukcje, jak pokazano w poniższym przykładzie.

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są odpięte i podlegają wyrzucaniu elementów bezużytecznych. W związku z tym nie należy wskazywać na te zmienne poza `fixed` instrukcją. Zmienne zadeklarowane w `fixed` instrukcji należą do zakresu tej instrukcji, ułatwiając to:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Wskaźniki inicjowane w `fixed` instrukcjach są zmiennymi tylko do odczytu. Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować ją. Nie można zmodyfikować zmiennej zadeklarowanej w `fixed` instrukcji:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Możesz przydzielić pamięć na stosie, gdzie nie podlega wyrzucaniu elementów bezużytecznych i dlatego nie musi być przypięty. Aby to zrobić, użyj [ `stackalloc` wyrażenia](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [FIXED Statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Odwołanie w C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [niebezpieczne](unsafe.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

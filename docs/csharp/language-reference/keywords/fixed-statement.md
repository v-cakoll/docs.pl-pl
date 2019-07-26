---
title: FIXED — C# odwołanie
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: d3c87f0e71095bbcc7c5a1d64b026e92838a6306
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433752"
---
# <a name="fixed-statement-c-reference"></a>fixed — Instrukcja (odwołanie w C#)

`fixed` Instrukcja zapobiega ponownemu lokalizowaniu ruchomej zmiennej przez moduł wyrzucania elementów bezużytecznych. Instrukcja jest dozwolona tylko w niebezpiecznym kontekście. [](unsafe.md) `fixed` Możesz również użyć słowa kluczowego, `fixed` aby utworzyć bufory o ustalonym [rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed` Instrukcja ustawia wskaźnik na zmienną zarządzaną i "pinezki", która jest zmienna podczas wykonywania instrukcji. Wskaźniki do ruchomych zmiennych zarządzanych są przydatne tylko w `fixed` kontekście. `fixed` Bez kontekstu, wyrzucanie elementów bezużytecznych może przewidzieć nieprzewidywalne zmienne. C# Kompilator umożliwia tylko przypisanie wskaźnika do zmiennej zarządzanej w `fixed` instrukcji.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Wskaźnik można zainicjować za pomocą tablicy, ciągu, buforu o ustalonym rozmiarze lub adresu zmiennej. Poniższy przykład ilustruje użycie adresów zmiennych, tablic i ciągów:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Począwszy od C# 7,3, `fixed` instrukcja działa na dodatkowych typach poza tablicami, ciągami, buforami o stałym rozmiarze lub zmiennymi niezarządzanymi. Każdy typ, który implementuje metodę o `GetPinnableReference` nazwie, może być przypięty. Musi zwracać zmienną typu niezarządzanego. [](../builtin-types/unmanaged-types.md) `GetPinnableReference` `ref` Typy <xref:System.Span%601?displayProperty=nameWithType> .NET i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> wprowadzone w środowisku .NET Core 2,0 używają tego wzorca i mogą być przypięte. Jest to pokazane w poniższym przykładzie:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Jeśli tworzysz typy, które powinny wchodzić w skład tego wzorca, zobacz <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> , aby zapoznać się z przykładem implementacji wzorca.

W jednej instrukcji można zainicjować wiele wskaźników, jeśli są one tego samego typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Aby zainicjować wskaźniki różnych typów, należy po prostu `fixed` zagnieżdżać instrukcje, jak pokazano w poniższym przykładzie.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są odpięte i podlegają wyrzucaniu elementów bezużytecznych. W związku z tym nie należy wskazywać na te `fixed` zmienne poza instrukcją. Zmienne zadeklarowane w `fixed` instrukcji należą do zakresu tej instrukcji, ułatwiając to:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Wskaźniki inicjowane `fixed` w instrukcjach są zmiennymi tylko do odczytu. Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować drugą zmienną wskaźnika i zmodyfikować ją. Nie można zmodyfikować zmiennej zadeklarowanej w `fixed` instrukcji:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Możesz przydzielić pamięć na stosie, gdzie nie podlega wyrzucaniu elementów bezużytecznych i dlatego nie musi być przypięty. W tym celu należy użyć [ `stackalloc` operatora](../operators/stackalloc.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [FIXED Statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [unsafe](unsafe.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

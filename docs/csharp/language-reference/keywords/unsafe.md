---
title: niebezpieczne słowo kluczowe C# — odwołanie
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712991"
---
# <a name="unsafe-c-reference"></a>unsafe (odwołanie w C#)

Słowo kluczowe `unsafe` oznacza niebezpieczny kontekst, który jest wymagany dla każdej operacji obejmującej wskaźniki. Aby uzyskać więcej informacji, zobacz artykuł [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).

Można użyć modyfikatora `unsafe` w deklaracji typu lub elementu członkowskiego. Cały tekstowy zakres typu lub elementu członkowskiego jest traktowany jako niebezpieczny kontekst. Na przykład poniżej przedstawiono metodę zadeklarowaną z modyfikatorem `unsafe`:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Zakres niebezpiecznego kontekstu rozciąga się od listy parametrów na koniec metody, dlatego na liście parametrów można również używać wskaźników:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Można również użyć niebezpiecznego bloku, aby umożliwić użycie niebezpiecznego kodu wewnątrz tego bloku. Na przykład:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Aby skompilować niebezpieczny kod, należy określić opcję kompilatora [`-unsafe`](../compiler-options/unsafe-compiler-option.md) . Kod niebezpieczny nie jest możliwy do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz artykuł [niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [fixed, instrukcja](fixed-statement.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)
- [Bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

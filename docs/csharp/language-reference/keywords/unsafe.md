---
title: słowa kluczowego unsafe (C# odwołania)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 79cb246c4094f02d1319d28fcc94d0d3d5bd9cb5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128430"
---
# <a name="unsafe-c-reference"></a>unsafe (odwołanie w C#)

`unsafe` — Słowo kluczowe określa niebezpieczny kontekst, który jest wymagany we wszystkich operacjach obejmujących wskaźniki. Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).

Możesz użyć `unsafe` modyfikatora w deklaracji typu lub elementu członkowskiego. W związku z tym niebezpieczny kontekst jest uważany za cały zakres tekstowa typu lub elementu członkowskiego. Na przykład, następujące jest zadeklarowana za pomocą metody `unsafe` modyfikator:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Zakres niebezpieczny kontekst rozciąga się od listy parametrów na końcu metody, więc wskaźniki można również na liście parametrów:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Blok niebezpieczne umożliwia również korzystanie z niebezpieczny kod wewnątrz tego bloku. Na przykład:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Aby skompilować kod niebezpieczny, należy określić [/ unsafe](../compiler-options/unsafe-compiler-option.md) — opcja kompilatora. Niebezpieczny kod nie jest możliwe do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [fixed, instrukcja](fixed-statement.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)
- [Bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
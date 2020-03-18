---
title: niebezpieczne słowo kluczowe — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712991"
---
# <a name="unsafe-c-reference"></a>unsafe (odwołanie w C#)

Słowo `unsafe` kluczowe oznacza niebezpieczny kontekst, który jest wymagany dla każdej operacji z udziałem wskaźników. Aby uzyskać więcej informacji, zobacz [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).

Modyfikatora `unsafe` można użyć w deklaracji typu lub elementu członkowskiego. Cały zakres tekstowy typu lub elementu członkowskiego jest zatem uważany za niebezpieczny kontekst. Na przykład, o to metoda `unsafe` zadeklarowana za pomocą modyfikatora:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Zakres niebezpiecznego kontekstu rozciąga się od listy parametrów do końca metody, więc wskaźniki mogą być również używane na liście parametrów:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Można również użyć niebezpiecznego bloku, aby włączyć użycie niebezpiecznego kodu wewnątrz tego bloku. Przykład:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Aby skompilować niebezpieczny kod, [`-unsafe`](../compiler-options/unsafe-compiler-option.md) należy określić opcję kompilatora. Niebezpieczny kod nie jest weryfikowalny przez program runtime języka wspólnego.

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [fixed, instrukcja](fixed-statement.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)
- [Bufory o stałym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)

---
title: Bufory o stałym rozmiarze — przewodnik programowania C#
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 6770497b23212f1786b4f4a620ed2b650079c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157029"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)

W języku C#, można użyć [stałej](../../language-reference/keywords/fixed-statement.md) instrukcji, aby utworzyć bufor z tablicą o stałym rozmiarze w strukturze danych. Bufory o stałym rozmiarze są przydatne podczas pisania metod, które współgrają ze źródłami danych z innych języków lub platform. Tablica stała może przyjmować dowolne atrybuty lub modyfikatory, które są dozwolone dla zwykłych elementów członkowskich struktury. Jedynym ograniczeniem jest to, `bool`że `byte` `char`typ `short` `int`tablicy `sbyte` `ushort`musi `uint` `ulong`być `float`, `double`, , `long`, , , , , lub .

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Uwagi

W bezpiecznym kodzie struktury C#, który zawiera tablicę nie zawiera elementów tablicy. Zamiast tego struktury zawiera odwołanie do elementów. Tablicę o stałym rozmiarze można osadzić w [strukturze,](../../language-reference/builtin-types/struct.md) gdy jest używana w [bloku kodu niebezpiecznego.](../../language-reference/keywords/unsafe.md)

Rozmiar następujących `struct` nie zależy od liczby elementów w tablicy, ponieważ `pathName` jest odwołanie:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

A `struct` może zawierać osadzoną tablicę w niebezpiecznym kodzie. W poniższym przykładzie `fixedBuffer` tablica ma stały rozmiar. Instrukcja `fixed` służy do ustanawiania wskaźnika do pierwszego elementu. Dostęp do elementów tablicy za pośrednictwem tego wskaźnika. Instrukcja `fixed` przypina `fixedBuffer` pole wystąpienia do określonej lokalizacji w pamięci.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

Rozmiar tablicy 128 `char` elementów wynosi 256 bajtów. Bufory [znaków](../../language-reference/builtin-types/char.md) o stałym rozmiarze zawsze przyjmują dwa bajty na znak, niezależnie od kodowania. Jest to prawdą nawet wtedy, gdy bufory char są organizowane `CharSet = CharSet.Auto` `CharSet = CharSet.Ansi`do metod interfejsu API lub struktur z lub . Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.

W poprzednim przykładzie przedstawiono `fixed` dostęp do pól bez przypinania, który jest dostępny począwszy od Języka C# 7.3.

Inną wspólną tablicą o stałym rozmiarze jest tablica [bool.](../../language-reference/builtin-types/bool.md) Elementy w `bool` tablicy są zawsze jeden bajt w rozmiarze. `bool`tablice nie są odpowiednie do tworzenia tablic bitowych lub buforów.

> [!NOTE]
> Z wyjątkiem pamięci utworzonej przy użyciu [stackalloc](../../language-reference/operators/stackalloc.md), kompilator C# i wywoływania języka wspólnego (CLR) nie wykonują żadnych kontroli przepełnienia buforu zabezpieczeń. Podobnie jak w każdym niebezpiecznym kodzie, należy zachować ostrożność.

Niebezpieczne bufory różnią się od zwykłych tablic w następujący sposób:

- Można używać tylko niebezpieczne bufory w kontekście niebezpieczne.
- Niebezpieczne bufory są zawsze wektorami lub tablicami jednowymiarowymi.
- Deklaracja tablicy powinna zawierać liczbę, `char id[8]`taką jak . Nie można `char id[]`użyć .
- Niebezpieczne bufory mogą być tylko pola wystąpienia struktur w niebezpiecznym kontekście.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [fixed, instrukcja](../../language-reference/keywords/fixed-statement.md)
- [Współdziałanie](../interop/index.md)

---
title: Bufory o ustalonym rozmiarze — Przewodnik programowania w języku C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 932ff3d57995ce47c4b74e8e888a479f0d09d0ed
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397431"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)

W języku C# można użyć instrukcji [FIXED](../../language-reference/keywords/fixed-statement.md) do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych. Bufory o ustalonym rozmiarze są przydatne podczas pisania metod, które współdziałają ze źródłami danych z innych języków lub platform. Stała tablica może przyjmować wszelkie atrybuty lub modyfikatory, które są dozwolone dla zwykłych elementów członkowskich struktury. Jedynym ograniczeniem jest to, że typem tablicy musi być,,,,,,,,,, `bool` `byte` `char` `short` `int` `long` `sbyte` `ushort` `uint` `ulong` `float` lub `double` .

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Uwagi

W bezpiecznym kodzie struktura języka C#, która zawiera tablicę, nie zawiera elementów tablicy. Zamiast tego, struktura zawiera odwołanie do elementów. Można osadzić tablicę o stałym rozmiarze w [strukturze](../../language-reference/builtin-types/struct.md) , gdy jest ona używana w [niebezpiecznym](../../language-reference/keywords/unsafe.md) bloku kodu.

Poniższe rozmiary `struct` nie zależą od liczby elementów w tablicy, ponieważ `pathName` jest odwołaniem:

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

`struct`Może zawierać osadzoną tablicę w niebezpiecznym kodzie. W poniższym przykładzie `fixedBuffer` Tablica ma stały rozmiar. Używasz instrukcji, `fixed` Aby nawiązać wskaźnik do pierwszego elementu. Dostęp do elementów tablicy można uzyskać za pomocą tego wskaźnika. `fixed`Instrukcja przypina `fixedBuffer` pole wystąpienia do określonej lokalizacji w pamięci.

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

Rozmiar tablicy elementów 128 `char` wynosi 256 bajtów. Bufory [znaków](../../language-reference/builtin-types/char.md) o stałym rozmiarze zawsze pobierają dwa bajty na znak, niezależnie od kodowania. Jest to prawdziwe nawet wtedy, gdy bufory char są organizowane do metod interfejsu API lub struktur z `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi` . Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.

W poprzednim przykładzie pokazano dostęp do `fixed` pól bez przypinania, które są dostępne od języka C# 7,3.

Inna wspólna tablica o stałym rozmiarze jest tablicą [logiczną](../../language-reference/builtin-types/bool.md) . Elementy w `bool` tablicy mają zawsze jeden bajt w rozmiarze. `bool`Tablice nie są odpowiednie do tworzenia tablic bitowych lub buforów.

Bufory o ustalonym rozmiarze są kompilowane przy użyciu <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> , który instruuje środowisko uruchomieniowe języka wspólnego (CLR), że typ zawiera niezarządzaną tablicę, która może być przepełnienia. Jest to podobne do pamięci utworzonej za pomocą [stackalloc](../../language-reference/operators/stackalloc.md), co powoduje automatyczne włączenie funkcji wykrywania przepełnienia buforu w środowisku CLR. W poprzednim przykładzie pokazano, jak bufor o ustalonym rozmiarze może istnieć w `unsafe struct` .

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

Kompilator wygenerował C# dla `Buffer` , ma następujący atrybut:

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

Bufory o ustalonym rozmiarze różnią się od zwykłych tablic w następujący sposób:

- Może być używany tylko w [niebezpiecznym](../../language-reference/keywords/unsafe.md) kontekście.
- Mogą to być tylko pola struktur.
- Są one zawsze wektorami lub tablic jednowymiarowych.
- Deklaracja powinna zawierać długość, taką jak `fixed char id[8]` . Nie można użyć `fixed char id[]` .

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [fixed, instrukcja](../../language-reference/keywords/fixed-statement.md)
- [Współdziałanie](../interop/index.md)

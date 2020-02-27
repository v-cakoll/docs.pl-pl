---
title: Bufory o ustalonym rozmiarze — C# Przewodnik programowania
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 9005c425badc5a4ed74e6af3447e563daf61229e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627802"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)

W C#programie można użyć instrukcji [FIXED](../../language-reference/keywords/fixed-statement.md) do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych. Bufory o ustalonym rozmiarze są przydatne podczas pisania metod, które współdziałają ze źródłami danych z innych języków lub platform. Stała tablica może przyjmować wszelkie atrybuty lub modyfikatory, które są dozwolone dla zwykłych elementów członkowskich struktury. Jedynym ograniczeniem jest to, że typ tablicy musi być `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`lub `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Uwagi

W bezpiecznym kodzie C# struktura, która zawiera tablicę, nie zawiera elementów tablicy. Zamiast tego, struktura zawiera odwołanie do elementów. Można osadzić tablicę o stałym rozmiarze w [strukturze](../../language-reference/builtin-types/struct.md) , gdy jest ona używana w [niebezpiecznym](../../language-reference/keywords/unsafe.md) bloku kodu.

Następująca `struct` ma rozmiar 8 bajtów. Tablica `pathName` jest odwołaniem:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

`struct` może zawierać osadzoną tablicę w niebezpiecznym kodzie. W poniższym przykładzie tablica `fixedBuffer` ma stały rozmiar. Użyj instrukcji `fixed`, aby określić wskaźnik do pierwszego elementu. Dostęp do elementów tablicy można uzyskać za pomocą tego wskaźnika. Instrukcja `fixed` przypina pole wystąpienia `fixedBuffer` do określonej lokalizacji w pamięci.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

Rozmiar elementu 128 `char` Array to 256 bajtów. Bufory [znaków](../../language-reference/builtin-types/char.md) o stałym rozmiarze zawsze pobierają dwa bajty na znak, niezależnie od kodowania. Jest to prawdziwe nawet wtedy, gdy bufory znaków są organizowane w metodach lub strukturach interfejsu API za pomocą `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi`. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.

W poprzednim przykładzie pokazano dostęp do pól `fixed` bez przypinania, które są dostępne C# od 7,3.

Inna wspólna tablica o stałym rozmiarze jest tablicą [logiczną](../../language-reference/builtin-types/bool.md) . Elementy w tablicy `bool` są zawsze w rozmiarze jednego bajtu. Tablice `bool` nie są odpowiednie do tworzenia tablic bitowych lub buforów.

> [!NOTE]
> Z wyjątkiem pamięci utworzonej przy użyciu [stackalloc](../../language-reference/operators/stackalloc.md), C# kompilator i środowisko uruchomieniowe języka wspólnego (CLR) nie wykonują żadnych kontroli przepełnienia buforu zabezpieczeń. Podobnie jak w przypadku całego niebezpiecznego kodu, należy zachować ostrożność.

Niebezpieczne bufory różnią się od zwykłych tablic w następujący sposób:

- W niebezpiecznym kontekście można używać tylko niebezpiecznych buforów.
- Niebezpieczne bufory są zawsze wektorami lub tablicami jednowymiarowymi.
- Deklaracja tablicy powinna zawierać liczbę, taką jak `char id[8]`. Nie można użyć `char id[]`.
- Niebezpieczne bufory mogą być wystąpieniami tylko pól struktur w niebezpiecznym kontekście.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [fixed, instrukcja](../../language-reference/keywords/fixed-statement.md)
- [Współdziałanie](../interop/index.md)

---
title: Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 310c5eed5507f75239efc78b6132fbc91211d29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339595"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)

W języku C#, można użyć [stałej](../../language-reference/keywords/fixed-statement.md) instrukcji do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych. Bufory o ustalonym rozmiarze są przydatne podczas pisania tego współdziałanie ze źródłami danych metody z innych języków lub platformy. Tablicy o ustalonym może zająć żadnych atrybutów ani modyfikatorów, które są dozwolone w przypadku elementów członkowskich struktury regularne. Tylko ograniczenie jest, że typ tablicy musi być `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, lub `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Uwagi

W kodzie bezpieczne struktury C#, który zawiera tablicę nie zawiera elementów tablicy. Struktura zawiera odwołania do elementów. Osadzić tablicy o ustalonym rozmiarze w [struktury](../../language-reference/keywords/struct.md) gdy jest używana w [niebezpieczne](../../language-reference/keywords/unsafe.md) blok kodu.

Następujące `struct` jest rozmiar 8 bajtów. `pathName` Tablica jest odwołanie:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

A `struct` może zawierać osadzoną tablicę w niebezpieczny kod. W poniższym przykładzie `fixedBuffer` tablicy ma stały rozmiar. Możesz użyć `fixed` instrukcji, aby ustanowić wskaźnik do pierwszego elementu. Elementy tablicy dostęp przez ten wskaźnik. `fixed` Numerów PIN instrukcji `fixedBuffer` pole wystąpienia w określonej lokalizacji w pamięci.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

Rozmiar elementu, 128 `char` tablicy to 256 bajtów. Stały rozmiar [char](../../language-reference/keywords/char.md) buforów zawsze pobierają dwa bajty na znak, niezależnie od tego, kodowania. Dotyczy to nawet, gdy buforów char są przekazywane do metody interfejsu API lub strukturach z `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi`. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.

W poprzednim przykładzie pokazano, uzyskiwanie dostępu do `fixed` pól bez przypinanie, które jest dostępnych w programie 7.3 C#.

Innej wspólnej tablicy o stałym rozmiarze jest [bool](../../language-reference/keywords/bool.md) tablicy. Elementy w `bool` tablicy są zawsze jednego bajtu rozmiar. `bool` tablice nie są odpowiednie do tworzenia tablic z bitowego lub buforów.

> [!NOTE]
> Z wyjątkiem pamięci utworzone za pomocą [stackalloc](../../language-reference/keywords/stackalloc.md), kompilator języka C# i środowisko uruchomieniowe języka wspólnego (CLR) nie wykonuj żadnych kontroli przepełnienie buforu zabezpieczeń. Podobnie jak w przypadku wszystkich niebezpieczny kod, należy zachować ostrożność.

Niebezpieczne bufory różnią się od regularne tablice w następujący sposób:

- Niebezpieczne bufory można używać tylko w niebezpiecznym kontekście.
- Niebezpieczne bufory są zawsze wektorów lub tablice jednowymiarowe.
- Deklaracja tablicy powinna zawierać liczbę, takich jak `char id[8]`. Nie można użyć `char id[]`.
- Niebezpieczne bufory można tylko pola wystąpienia struktur w niebezpiecznym kontekście.

## <a name="see-also"></a>Zobacz też

[Przewodnik programowania w języku C#](../index.md)  
[Niebezpieczny kod i wskaźniki](index.md)  
[fixed, instrukcja](../../language-reference/keywords/fixed-statement.md)  
[Współdziałanie](../interop/index.md)

---
title: Ustalony rozmiar buforów - C# przewodnik programowania
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 2d0a4f829f6fe4d9662e25a4d8fd3936d2afd7f1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242487"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)

W języku C#, można użyć [stałej](../../language-reference/keywords/fixed-statement.md) instrukcję, aby utworzyć buforu z tablicą o stałym rozmiarze w strukturze danych. Bufory o ustalonym rozmiarze są przydatne, kiedy piszesz metod tego współdziałania ze źródłami danych z innych języków lub platform. Naprawiono tablicy może potrwać atrybuty ani modyfikatorów, których można używać do elementów członkowskich struktury regularne. Jedynym ograniczeniem jest to, że typ tablicy musi być `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, lub `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Uwagi

W kodzie bezpiecznym struktury języka C#, która zawiera tablicę nie zawiera elementów tablicy. Struktura zawiera odwołania do elementów. Możesz osadzić tablicy o stałym rozmiarze w [struktury](../../language-reference/keywords/struct.md) gdy jest używany w [niebezpieczne](../../language-reference/keywords/unsafe.md) bloku kodu.

Następujące `struct` jest 8 bajtów. `pathName` Tablica jest odwołanie:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

Element `struct` może zawierać osadzoną tablicę w niebezpieczny kod. W poniższym przykładzie `fixedBuffer` tablica ma stały rozmiar. Możesz użyć `fixed` instrukcję, aby ustanowić wskaźnik do pierwszego elementu. Możesz uzyskać dostęp do elementów tablicy za pomocą tego wskaźnika. `fixed` Numerów PIN instrukcji `fixedBuffer` pola wystąpienia w określonej lokalizacji w pamięci.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

Rozmiar elementu 128 `char` tablicy to 256 bajtów. Ustalony rozmiar [char](../../language-reference/keywords/char.md) buforów zawsze pobierają dwóch bajtów na znak, niezależnie od tego, kodowania. Ta zasada obowiązuje nawet po buforów char są wysyłane do metody interfejsu API lub struktury z `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi`. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.

W poprzednim przykładzie pokazano, uzyskiwanie dostępu do `fixed` bez przypinania, pola, których jest dostępna, począwszy od C# 7.3.

Innej wspólnej tablicy o stałym rozmiarze jest [bool](../../language-reference/keywords/bool.md) tablicy. Elementy w `bool` tablicy są zawsze jednobajtowego w rozmiarze. `bool` tablice nie są odpowiednie do tworzenia tablic bitowe lub buforów.

> [!NOTE]
> Z wyjątkiem pamięci utworzone za pomocą [stackalloc](../../language-reference/keywords/stackalloc.md), kompilator języka C# i środowisko uruchomieniowe języka wspólnego (CLR) nie sprawdza zabezpieczeń buforu przepełnienia. Podobnie jak w przypadku wszystkich niebezpieczny kod, należy zachować ostrożność.

Niebezpieczne bufory różnią się od regularnych tablic w następujący sposób:

- Niebezpieczne bufory można używać tylko w niebezpiecznym kontekście.
- Niebezpieczne bufory są zawsze wektorów lub tablic jednowymiarowych.
- Deklaracja tablicy powinna zawierać liczbę, takich jak `char id[8]`. Nie można użyć `char id[]`.
- Niebezpieczne bufory można tylko wystąpienia pól struktur w niebezpiecznym kontekście.

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)  
- [Niebezpieczny kod i wskaźniki](index.md)  
- [fixed, instrukcja](../../language-reference/keywords/fixed-statement.md)  
- [Współdziałanie](../interop/index.md)

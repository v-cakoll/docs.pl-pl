---
title: "Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Bufory o ustalonym rozmiarze (Przewodnik programowania w języku C#)
W języku C#, można użyć [stałej](../../../csharp/language-reference/keywords/fixed-statement.md) instrukcji do utworzenia buforu z tablicą o stałym rozmiarze w strukturze danych. Jest to przydatne podczas pracy z istniejącym kodem, takie jak kod napisany w innych językach w istniejącym bibliotek DLL i COM projektów. Tablicy o ustalonym może zająć żadnych atrybutów ani modyfikatorów, które są dozwolone w przypadku elementów członkowskich struktury regularne. Tylko ograniczenie jest, że typ tablicy musi być `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, lub `double`.  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a>Uwagi  
 Wczesne wersji języka C# deklarowanie struktury stałym rozmiarze styl C++ było trudne ponieważ struktury C#, który zawiera tablicę nie zawiera elementów tablicy. Struktura zawiera odwołania do elementów.  
  
 C# 2.0 dodano możliwość osadzania tablicy o ustalonym rozmiarze w [struktury](../../../csharp/language-reference/keywords/struct.md) gdy jest używana w [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) blok kodu.  
  
 Na przykład przed C# 2.0, następujące `struct` byłoby o rozmiarze 8 bajtów. `pathName` Tablica jest odwołanie do tablicy przydzielone stosu:  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 Począwszy od C# 2.0, `struct` może zawierać osadzoną tablicę. W poniższym przykładzie `fixedBuffer` tablicy ma stały rozmiar. Aby uzyskać dostęp do elementów tablicy, należy użyć `fixed` instrukcji, aby ustanowić wskaźnik do pierwszego elementu. `fixed` Instrukcji PIN wystąpienia `fixedBuffer` do określonej lokalizacji w pamięci.  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 Rozmiar elementu, 128 `char` tablicy to 256 bajtów. Stały rozmiar [char](../../../csharp/language-reference/keywords/char.md) buforów zawsze pobierają dwa bajty na znak, niezależnie od tego, kodowania. Dotyczy to nawet, gdy buforów char są przekazywane do metody interfejsu API lub strukturach z `CharSet = CharSet.Auto` lub `CharSet = CharSet.Ansi`. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.InteropServices.CharSet>.  
  
 Innej wspólnej tablicy o stałym rozmiarze jest [bool](../../../csharp/language-reference/keywords/bool.md) tablicy. Elementy w `bool` tablicy są zawsze jednego bajtu rozmiar. `bool`tablice nie są odpowiednie do tworzenia tablic z bitowego lub buforów.  
  
> [!NOTE]
>  Z wyjątkiem pamięci utworzone za pomocą [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), kompilator języka C# i środowisko uruchomieniowe języka wspólnego (CLR) nie wykonuj żadnych kontroli przepełnienie buforu zabezpieczeń. Podobnie jak w przypadku wszystkich niebezpieczny kod, należy zachować ostrożność.  
  
 Niebezpieczne bufory różnią się od regularne tablice w następujący sposób:  
  
-   Niebezpieczne bufory można używać tylko w niebezpiecznym kontekście.  
  
-   Niebezpieczne bufory są zawsze wektorów lub tablice jednowymiarowe.  
  
-   Deklaracja tablicy powinna zawierać liczbę, takich jak `char id[8]`. Nie można użyć `char id[]` zamiast tego.  
  
-   Niebezpieczne bufory można tylko pola wystąpienia struktur w niebezpiecznym kontekście.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Fixed — instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Współdziałanie](../../../csharp/programming-guide/interop/index.md)

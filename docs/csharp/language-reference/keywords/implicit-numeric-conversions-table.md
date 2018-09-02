---
title: Tabela niejawnych konwersji liczbowych (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 4bbc6086dc5fd3838ef9361762c3068ca44efd0e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417599"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabela niejawnych konwersji liczbowych (odwołanie w C#)
W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawnych konwersji liczbowych. Niejawne konwersje mogą wystąpić w wielu sytuacjach, w tym metody wywoływania i przypisania poufności informacji.  
  
|Z|Zadanie|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`, `int`, `long`, `float`, `double`, lub `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`, `long`, `float`, `double`, lub `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`, `float`, `double`, lub `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`, `ulong`, `float`, `double`, lub `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`, `double`, lub `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`, `double`, lub `decimal`|  
  
## <a name="remarks"></a>Uwagi  
  
-   Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.  
  
-   Brak konwersji niejawnych do `char` typu.  
  
-   Brak niejawnej konwersji między typami zmiennoprzecinkowymi a `decimal` typu.  
  
-   Wyrażenie stałe typu `int` mogą być konwertowane na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, o ile wartości stałe wyrażenia znajduje się w zakresie miejsca docelowego Typ.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)

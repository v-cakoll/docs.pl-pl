---
title: "uint (odwołanie w C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d32f7146d1f9e13d8cf0f275f4fd78b693b09d31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="uint-c-reference"></a>uint (odwołanie w C#)

`uint` — Słowo kluczowe oznacza, że typ całkowity, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ programu .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`uint`|4 294 967 0 Aby 295|Liczba całkowita 32-bitowa bez znaku|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 **Uwaga** `uint` typu nie jest zgodne ze specyfikacją CLS. Użyj `int` zawsze, gdy jest to możliwe.  
  
## <a name="literals"></a>Literały  

Można zadeklarować i zainicjuj `uint` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od C# 7) literału do niego dane binarne. Jeśli liczba całkowita literału jest poza zakresem `uint` (to znaczy, jeśli jest mniejszy niż <xref:System.UInt32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 3,000,000,000, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `uint` wartości.  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny. Literałów dziesiętnych mają nie ma prefiksu. 

Począwszy od C# 7, dodano kilka funkcji w celu zwiększenia czytelności. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie. Literał dziesiętny nie mogą mieć wiodące podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 Literały całkowite mogą również obejmować sufiks, który wskazuje typ. Sufiks `U` lub "u" oznacza albo `uint` lub `ulong`, w zależności od liczbowa wartość literału. W poniższym przykładzie użyto `u` sufiks określający całkowitą bez znaku obu typów. Należy zauważyć, że pierwszy literał `uint` , ponieważ jej wartość jest mniejsza niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a drugą jest wartość `ulong` , ponieważ jej wartość jest większa niż <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
Jeśli literał całkowity nie sufiks, jego typ jest pierwszy następujących typów, w których może być reprezentowany wartość: 

1. [int](int.md)
2. `uint`
3. [długa](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `uint` do [długi](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [ decimal](../../../csharp/language-reference/keywords/decimal.md). Na przykład:  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 Jest wstępnie zdefiniowanych niejawna konwersja z [bajtów](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), lub [char](../../../csharp/language-reference/keywords/char.md) do `uint`. W przeciwnym razie należy użyć rzutowanie. Na przykład następująca instrukcja przypisania spowoduje błąd kompilacji bez rzutowanie:  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 Spójrz również, że nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `uint`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).  
  
 Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [niejawne numeryczne Tabela konwersji](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.UInt32>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

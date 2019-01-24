---
title: int — C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: b1a621b7cce61ecd2c26c72adbdc3aa56749c914
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615653"
---
# <a name="int-c-reference"></a>int (odwołanie w C#)

`int` Wskazuje, że integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ architektury .NET|  
|----------|-----------|----------|-------------------------|  
|`int`|-2 147 483 2 147 483 648 do 647|32-bitowa liczba całkowita ze znakiem|<xref:System.Int32?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały  
 
Można zadeklarować i zainicjować `int` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.  Jeśli literał liczby całkowitej jest poza zakresem `int` (to znaczy, jeśli jest mniejszy niż <xref:System.Int32.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int32.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji. 

W poniższym przykładzie liczb całkowitych równa 90,946, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `int` wartości.  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego. Literały dziesiętna mieć żadnego prefiksu. 

Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie. Literał dziesiętny nie mogą mieć wiodącego podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 Literały całkowite mogą również zawierać sufiks, który oznacza typ., mimo że istnieje nie przyrostka, który oznacza `int` typu. Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana: 

1. `int`
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
 
W tych przykładach 90946 literał jest typu `int`.
  
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `int` do [długie](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md). Na przykład:  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 Jest wstępnie zdefiniowanych niejawna konwersja z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), lub [char](../../../csharp/language-reference/keywords/char.md) Aby `int`. Na przykład poniższa instrukcja przypisania spowoduje błąd kompilacji bez rzutowania:  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `int`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 Aby uzyskać więcej informacji na wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Int32>
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

---
title: "long (odwołanie w C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f18bed80550b293195961fd9d42491dd571cbaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="long-c-reference"></a>long (odwołanie w C#)

`long`Określa typ całkowity, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ programu .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`long`|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|64-bitowa liczba całkowita|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały 

Można zadeklarować i zainicjuj `long` zmiennej przypisując literał dziesiętny literałem szesnastkową lub (począwszy od C# 7) literału do niego dane binarne. 

W poniższym przykładzie liczb całkowitych równa 4 294 967 296, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są przypisane do `long` wartości.  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowe literału i prefiks `0b` lub `0B` do oznaczania literał binarny. Literałów dziesiętnych mają nie ma prefiksu. 

Począwszy od C# 7, dodano kilka funkcji w celu zwiększenia czytelności. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - C# 7.2 umożliwia `_` ma być używany jako separator cyfr dla literału binary lub szesnastkowe po prefiksie. Literał dziesiętny nie mogą mieć wiodące podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Literały całkowite mogą również obejmować sufiks, który wskazuje typ. Sufiks `L` oznacza `long`. W poniższym przykładzie użyto `L` sufiks określający długich liczb całkowitych:
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  Mała litera "l" można także używać jako sufiks. Jednak generuje ostrzeżenie kompilatora ponieważ litera "l" można łatwo pomylić z cyfrą "1". Dla uzyskania przejrzystości, należy użyć "L".  
  
 Kiedy używać sufiksu `L`, typ literału liczb całkowitych jest określony jako albo `long` lub [ulong](../../../csharp/language-reference/keywords/ulong.md), w zależności od rozmiaru. W takim przypadku jest `long` ponieważ ona mniejsza niż zakres [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Zazwyczaj sufiksu jest używane do wywołania metody przeciążone. Na przykład następujące przeciążone metody ma parametry typu `long` i [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 `L` Sufiks gwarantuje nosi poprawne przeciążenia:  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
Jeśli literał całkowity nie sufiks, jego typ jest pierwszy następujących typów, w których może być reprezentowany wartość: 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 

Jest typu literal 4294967296 w poprzednich przykładach `long`, ponieważ jego rozmiar przekracza zakres [uint](../../../csharp/language-reference/keywords/uint.md) (zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md) dla rozmiaru magazynu typów całkowitych).  
  
 Jeśli używasz `long` typu z innych typów całkowitych w tym samym wyrażeniu wyrażenie jest obliczane jako `long` (lub [bool](../../../csharp/language-reference/keywords/bool.md) w przypadku wyrażeń relacyjnych lub wartość logiczna). Na przykład poniższe wyrażenie obliczane jako `long`:  
  
```csharp  
898L + 88  
```  
  
 Informacje w wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [podwójne](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `long` do [float](../../../csharp/language-reference/keywords/float.md), [podwójne](../../../csharp/language-reference/keywords/double.md), lub [dziesiętną](../../../csharp/language-reference/keywords/decimal.md). W przeciwnym razie należy użyć rzutowanie. Na przykład następująca instrukcja spowoduje błąd kompilacji bez jawnego rzutowania:  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Jest wstępnie zdefiniowanych niejawna konwersja z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), lub [char](../../../csharp/language-reference/keywords/char.md) do `long`.  
  
 Spójrz również, że nie jest niejawna konwersja z typów zmiennoprzecinkowych aby `long`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Int64>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

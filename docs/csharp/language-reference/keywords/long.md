---
title: long (odwołanie w C#)
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: 52755e0914ead3ab61930dd8bfb9ecdd8ced0a14
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400839"
---
# <a name="long-c-reference"></a>long (odwołanie w C#)

`long` Wskazuje, że integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ architektury .NET|  
|----------|-----------|----------|-------------------------|  
|`long`|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|64-bitowa liczba całkowita ze znakiem|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały 

Można zadeklarować i zainicjować `long` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne. 

W poniższym przykładzie liczb całkowitych równa 4 294 967 296, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `long` wartości.  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego. Literały dziesiętna mieć żadnego prefiksu. 

Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie. Literał dziesiętny nie mogą mieć wiodącego podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Literały całkowite mogą również zawierać sufiks, który oznacza typ. Sufiks `L` oznacza `long`. W poniższym przykładzie użyto `L` sufiks do oznaczania długich liczb całkowitych:
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  Mała litera "l" można również użyć jako sufiks. Jednakże spowoduje to wygenerowanie ostrzeżenia kompilatora ponieważ litera "l" można łatwo pomylić z cyfrą "1". Użyj "L" w celu uściślenia.  
  
 Kiedy używasz sufiks `L`, typu literał liczby całkowitej zostanie uznane albo `long` lub [ulong](../../../csharp/language-reference/keywords/ulong.md), w zależności od rozmiaru. W tym przypadku jest to `long` ponieważ ona mniejsza niż zakres [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Zazwyczaj sufiksu jest używane do wywołania przeciążonych metod. Na przykład mieć parametrów typu w następujących przeciążonych metod `long` i [int](../../../csharp/language-reference/keywords/int.md):  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 `L` Sufiks gwarantuje, że poprawne przeciążenie jest wywoływana:  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana: 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 

Typem jest literał 4294967296 w poprzednich przykładach `long`, ponieważ spowodowałoby to przekroczenie zakresu [uint](../../../csharp/language-reference/keywords/uint.md) (zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md) dla rozmiaru magazynu typów całkowitych).  
  
 Jeśli używasz `long` typu o inne typy całkowitoliczbowe w jednym wyrażeniu, wyrażenie jest oceniane jako `long` (lub [bool](../../../csharp/language-reference/keywords/bool.md) w przypadku wyrażeń relacyjnych lub logiczną). Na przykład poniższe wyrażenie obliczane jako `long`:  
  
```csharp  
898L + 88  
```  
  
 Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `long` do [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md). W przeciwnym razie należy użyć rzutowania. Na przykład następująca instrukcja generuje błąd kompilacji bez jawnego rzutowania:  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int y = (int)8L;   // OK: explicit conversion to int  
```  
  
 Jest wstępnie zdefiniowanych niejawna konwersja z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), lub [char](../../../csharp/language-reference/keywords/char.md) do `long`.  
  
 Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `long`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Int64>  
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

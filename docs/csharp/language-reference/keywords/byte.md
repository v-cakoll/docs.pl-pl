---
title: Byte — C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 9c70c5a08e1509e9c8b1a007603abfbf18f03f14
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241241"
---
# <a name="byte-c-reference"></a>byte (odwołanie w C#)

`byte` Wskazuje, że integralny typ, który przechowuje wartości, jak wskazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ architektury .NET|  
|----------|-----------|----------|-------------------------|  
|`byte`|od 0 do 255|Liczba całkowita bez znaku 8-bitowa|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały  

 Można zadeklarować i zainicjować `byte` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne. Jeśli literał liczby całkowitej jest poza zakresem `byte` (to znaczy, jeśli jest mniejszy niż <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Byte.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 201, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `byte` wartości.    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego. Literały dziesiętna mieć żadnego prefiksu.

Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie. Literał dziesiętny nie mogą mieć wiodącego podkreślenia.

Poniżej przedstawiono kilka przykładów.

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `byte` do [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi ](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nie można niejawnie przekonwertować literału liczbowego rodzaje większy rozmiar magazynu na `byte`. Aby uzyskać więcej informacji na temat rozmiarów pamięci masowej typów całkowitych, zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md). Należy wziąć pod uwagę, na przykład, następujące dwa `byte` zmienne `x` i `y`:  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 Poniższa instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania `int` domyślnie.  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Aby rozwiązać ten problem, należy użyć rzutowania:  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Możliwe jest jednak zastosować następujące instrukcje, w którym Zmienna docelowa ma taki sam rozmiar magazynu lub większy rozmiar magazynu:  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Ponadto istnieje niejawna konwersja z typów zmiennoprzecinkowych `byte`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Podczas wywoływania metody przeciążonej, należy użyć rzutowania. Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `byte` i [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 Za pomocą `byte` rzutowania gwarantuje, że poprawnego typu ma nazwę, na przykład:  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).  
  
 Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też  

- <xref:System.Byte>  
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

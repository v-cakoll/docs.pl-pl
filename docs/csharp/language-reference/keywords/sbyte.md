---
title: SByte — C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
ms.openlocfilehash: e7dc10706257b2c1fa8574f193523272339f61ff
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242857"
---
# <a name="sbyte-c-reference"></a>sbyte (odwołanie w C#)

`sbyte` Wskazuje, że integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.  
  
|Typ|Zakres|Rozmiar|Typ architektury .NET|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 do 127 znaków.|8-bitową liczbę całkowitą ze znakiem|<xref:System.SByte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały  

Można zadeklarować i zainicjować `sbyte` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne. 

W poniższym przykładzie liczb całkowitych równa-102, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są konwertowane z [int](../../../csharp/language-reference/keywords/int.md) do `sbyte` wartości.    
  
[!code-csharp[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]  

> [!NOTE] 
> Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego. Literały dziesiętna mieć żadnego prefiksu.

Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność. 
 - C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.
 - Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie. Literał dziesiętny nie mogą mieć wiodącego podkreślenia.

 Poniżej przedstawiono kilka przykładów.

[!code-csharp[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]  

Jeśli literał liczby całkowitej jest poza zakresem `sbyte` (to znaczy, jeśli jest mniejszy niż <xref:System.SByte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.SByte.MaxValue?displayProperty=nameWithType>, występuje błąd kompilacji. Gdy literał liczby całkowitej jest brak przyrostka, jego typ jest to pierwsza z tych typów, w których jej wartość może być reprezentowana: [int](int.md), [uint](uint.md), [długie](long.md), [ulong](ulong.md). Oznacza to, że w tym przykładzie literały numeryczne `0x9A` i `0b10011010` są interpretowane jako 32-bitowe liczby całkowite ze znakiem z wartością 156, co powoduje przekroczenie <xref:System.SByte.MaxValue?displayProperty=nameWithType>. W związku z tym operatora rzutowania są potrzebne, i przypisanie musi występować w [unchecked](unchecked.md) kontekstu. 

## <a name="compiler-overload-resolution"></a>Przeciążeń z późnym

 Podczas wywoływania przeciążone metody, należy użyć rzutowania. Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `sbyte` i [int](../../../csharp/language-reference/keywords/int.md) parametry:  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 Za pomocą `sbyte` rzutowania gwarantuje, że poprawnego typu ma nazwę, na przykład:  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>Konwersje  
 Jest wstępnie zdefiniowanych niejawna konwersja z `sbyte` do [krótki](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [długie](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double ](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md).  
  
 Nie można niejawnie przekonwertować nieliteralnego typy liczbowe większy rozmiar magazynu na `sbyte` (zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md) dla rozmiaru magazynu typów całkowitych). Należy wziąć pod uwagę, na przykład, następujące dwa `sbyte` zmienne `x` i `y`:  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 Poniższa instrukcja przypisania spowoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania [int](../../../csharp/language-reference/keywords/int.md) domyślnie.  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 Aby rozwiązać ten problem, rzutowane wyrażenia, jak w poniższym przykładzie:  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 Możliwe jest jednak należy zastosować następujące polecenia, gdzie zmienna docelowa ma taki sam rozmiar magazynu lub większy rozmiar magazynu:  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `sbyte`. Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 Aby uzyskać informacje o wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).  
  
 Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- <xref:System.SByte>  
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

---
title: double (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 3683b51dfd0ef653ab8bfff6705b96a37e21a10a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="double-c-reference"></a>double (odwołanie w C#)
`double` — Słowo kluczowe oznacza typu prostego, która przechowuje 64-bitowych wartości zmiennoprzecinkowych. W poniższej tabeli przedstawiono dokładność i zakres przybliżonej `double` typu.  
  
|Typ|Zakresie|Dokładność|Typ programu .NET Framework|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|±5.0 x 10<sup>−324</sup> do ±1.7 x 10<sup>308</sup>|15-16 cyfr|<xref:System.Double?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literały  
 Domyślnie rzeczywistym literałem po prawej stronie operatora przypisania jest traktowany jako `double`. Jednak jeśli mają być traktowane jako liczba całkowita z zakresu `double`, należy użyć sufiksu d lub D, na przykład:  
  
```csharp  
double x = 3D;  
```  
  
## <a name="conversions"></a>Konwersje  
 Można mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu. W takim przypadku typów całkowitych są konwertowane na typów zmiennoprzecinkowych. Obliczanie wyrażenia odbywa się zgodnie z następującymi zasadami:  
  
-   Po spełnieniu jednego z typów zmiennoprzecinkowych `double`, wyrażenie ma `double`, lub [bool](../../../csharp/language-reference/keywords/bool.md) w wyrażeniach relacyjnych lub Boolean.  
  
-   W przypadku nie `double` typ w wyrażeniu, ocenia się [float](../../../csharp/language-reference/keywords/float.md), lub [bool](../../../csharp/language-reference/keywords/bool.md) w wyrażeniach relacyjnych lub Boolean.  
  
 Zmiennoprzecinkowe wyrażenie może zawierać następujące zestawy wartości:  
  
-   Zero dodatnie i ujemne.  
  
-   Dodatnie i ujemne nieskończoności.  
  
-   Wartość nie-liczby (NaN).  
  
-   Ograniczone zestaw niezerowe wartości.  
  
 Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne Floating-Point operacje arytmetyczne, dostępnych na [IEEE](http://www.ieee.org) witryny sieci Web.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie [int](../../../csharp/language-reference/keywords/int.md), [krótki](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md), a `double` są dodawane, jednocześnie zapewniając `double` wynik.  
  
 [!code-csharp[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela typów zmiennoprzecinkowych](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

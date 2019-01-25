---
title: Porównywanie równości - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: 25ac904b848311639dda1ecf231f0d6565799733
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620178"
---
# <a name="equality-comparisons-c-programming-guide"></a>Porównywanie równości (Przewodnik programowania w języku C#)
Czasami jest konieczne porównanie dwóch wartości dla równości. W niektórych przypadkach testuje się *wartość równości*, znane również jako *równoważności*, co oznacza, że wartości, które są zawarte w dwóch zmiennych są równe. W innych przypadkach należy ustalić, czy dwie zmienne odnoszą się do tego samego podstawowego obiektu w pamięci. Ten typ równości jest nazywany *równości odwołań*, lub *tożsamości*. Ten temat opisuje te dwa rodzaje równości i zawiera łącza do innych tematów, aby uzyskać więcej informacji.  
  
## <a name="reference-equality"></a>Równość odniesienia  
 Równość odniesienia oznacza, że dwa odwołania do obiektu odnoszą się do tego samego obiektu podstawowego. Taka sytuacja może wystąpić poprzez proste zadanie, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]  
  
 W tym kodzie tworzone są dwa obiekty, ale po instrukcji przypisania, oba odwołania odnoszą się do tego samego obiektu. W związku z tym mają odniesienie równości. Użyj <xref:System.Object.ReferenceEquals%2A> metodę pozwala ustalić, czy dwa odwołania odwołują się do tego samego obiektu.  
  
 Koncepcja odwołania dotyczy tylko typów odwołań. Obiekty typu wartości nie może mieć równości odwołań, ponieważ wystąpienie typu wartości jest przypisane do zmiennej, kopię wartości są tworzone. W związku z tym nie można nigdy posiadać dwóch struct bez opakowania, które odwołują się do tej samej lokalizacji w pamięci. Ponadto jeśli używasz <xref:System.Object.ReferenceEquals%2A> do porównywania dwóch typów wartości, wynik będzie zawsze `false`nawet wtedy, gdy wartości, które są zawarte w obiektach są identyczne. Jest to spowodowane każda zmienna jest umieszczona w osobnym wystąpieniu obiektu. Aby uzyskać więcej informacji, zobacz [jak: Testowanie równości odwołań (tożsamości)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).  
  
## <a name="value-equality"></a>Równość wartości  
 Równość wartości oznacza, że dwa obiekty zawierają tę samą wartość lub wartości. Dla podstawowych typów wartości takie jak [int](../../../csharp/language-reference/keywords/int.md) lub [bool](../../../csharp/language-reference/keywords/bool.md), testy na równoważność wartości są proste. Możesz użyć [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) operatora, jak pokazano w poniższym przykładzie.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Dla większości innych typów testowanie równoważności wartości jest bardziej złożone, ponieważ wymaga, że rozumiesz, jak typ Określa go. Dla klas i struktur mających wiele pól lub właściwości, wartość jest często definiowana równość oznacza, że wszystkie pola lub właściwości mają taką samą wartość. Na przykład dwa `Point` obiekty mogą być zdefiniowane jako równoważne, jeżeli pointA.X jest równy pointB.X i pointA.Y jest równy pointb.y.  
  
 Jednak istnieje wymóg że równoważność musi opierać się na wszystkie pola w typie. Może być on oparty na podzbiorze. Przy porównaniu typów, które nie są jego własnością, należy pamiętać zrozumieć, w szczególności jest definiowanie równoważności dla tego typu. Aby uzyskać więcej informacji na temat sposobu definiowania równości wartości własnych klas i struktur, zobacz [jak: Definiowanie równości wartości dla typu](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).  
  
### <a name="value-equality-for-floating-point-values"></a>Równość wartości dla wartości zmiennoprzecinkowych  
 Porównania równości pływających punktu wartości ([double](../../../csharp/language-reference/keywords/double.md) i [float](../../../csharp/language-reference/keywords/float.md)) są problematyczne ze względu na niedokładności pływających punktów arytmetycznych na komputerach binarnych. Aby uzyskać więcej informacji, zobacz uwagi w temacie <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Testowanie równości odwołań (tożsamości)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|W tym artykule opisano, jak ustalić, czy dwie zmienne mają odniesienie równości.|  
|[Instrukcje: Definiowanie równości wartości dla typu](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|Opisuje sposob dostarczania niestandardowych definicji równości wartość dla typu.|  
|[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)|Zawiera łącza do szczegółowych informacji o ważnych funkcjach języka C# i funkcje, które są dostępne dla języka C# za pomocą programu .NET Framework.|  
|[Typy](../../../csharp/programming-guide/types/index.md)|Zawiera informacje o systemie typu C# i linki do dodatkowych informacji.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)

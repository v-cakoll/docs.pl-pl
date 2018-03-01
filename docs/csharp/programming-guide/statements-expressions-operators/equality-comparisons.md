---
title: "Porównywanie równości (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 199257b1fe371dea3e4ee1eedcf11f3bdce02366
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="equality-comparisons-c-programming-guide"></a>Porównywanie równości (Przewodnik programowania w języku C#)
Czasami jest niezbędne do porównywania dwóch wartości pod kątem równości. W niektórych przypadkach testowych dla *wartość równości*, znanej także jako *ekwiwalencji*, co oznacza, że wartości, które znajdują się w dwóch zmiennych są takie same. W innych przypadkach należy ustalić, czy dwie zmienne odwoływać się do tego samego obiektu źródłowego w pamięci. Równości tego typu jest nazywana *odwołania równości*, lub *tożsamości*. W tym temacie opisano te dwa rodzaje równości oraz zawiera łącza do innych tematów, aby uzyskać więcej informacji.  
  
## <a name="reference-equality"></a>Równość odwołania  
 Równość odwołania oznacza, że dwa odwołania do obiektów odwołują się do tego samego obiektu źródłowego. Taka sytuacja może wystąpić przez przypisanie proste, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideStatements#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/equality-comparisons_1.cs)]  
  
 W tym kodzie dwa obiekty są tworzone, ale po instrukcji przypisania, oba odwołania dotyczą tego samego obiektu. W związku z tym mają równości odwołań. Użyj <xref:System.Object.ReferenceEquals%2A> metodę, aby określić, czy dwa odwołania odnoszą się do tego samego obiektu.  
  
 Odwołanie równości dotyczy tylko typy referencyjne. Obiekty typu wartości nie może mieć równości odwołań, ponieważ gdy wystąpienia typu wartości jest przypisany do zmiennej, możliwe jest kopią wartości. W związku z tym nigdy nie może mieć dwóch rozpakowany struktur, które odwołują się do tej samej lokalizacji w pamięci. Ponadto jeśli używasz <xref:System.Object.ReferenceEquals%2A> Aby porównać dwa typy wartości, wynik będzie zawsze równa `false`nawet wtedy, gdy wartości, które są zawarte w obiektach są wszystkie identyczne. Jest to spowodowane każdej zmiennej jest opakowany do wystąpienia oddzielny obiekt. Aby uzyskać więcej informacji, zobacz [porady: testowanie równości odwołań (tożsamości)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).  
  
## <a name="value-equality"></a>Równość wartości  
 Równość wartości oznacza, że dwa obiekty zawierają tę samą wartość lub wartości. Dla wartości pierwotnych typów takich jak [int](../../../csharp/language-reference/keywords/int.md) lub [bool](../../../csharp/language-reference/keywords/bool.md), testów dla równości wartości są oczywiste. Można użyć [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) operatora, jak pokazano w poniższym przykładzie.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 Dla większości innych typów testowanie pod kątem równości wartości jest bardziej złożony ponieważ wymaga ona, że rozumiesz, jak typ definiuje ją. Dla klas i struktur, który ma wiele pól lub właściwości równości wartości jest zdefiniowany często oznacza, że wszystkie pola lub właściwości mają taką samą wartość. Na przykład dwa `Point` można zdefiniować obiekty jako równoważne, jeśli równą pointB.X pointA.X i pointA.Y jest równa pointB.Y.  
  
 Istnieje jednak wymóg równoważność podstawą wszystkich pól w typie. Może być oparta na podzbiorze. Podczas porównywania typów, które nie ma, należy upewnić zrozumieć, w szczególności, jak równoważność jest zdefiniowany dla tego typu. Aby uzyskać więcej informacji o sposobie Definiowanie równości wartości w własnych klas i struktur, zobacz [porady: Definiowanie równości wartości dla typu](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).  
  
### <a name="value-equality-for-floating-point-values"></a>Równości wartości dla wartości zmiennoprzecinkowych  
 Porównania równości zmiennoprzecinkową punktu wartości ([podwójne](../../../csharp/language-reference/keywords/double.md) i [float](../../../csharp/language-reference/keywords/float.md)) mogą powodować problemy z powodu błędu z zmiennoprzecinkową punktu arytmetycznego na komputerach binarnego. Aby uzyskać więcej informacji, zobacz uwagi w temacie <xref:System.Double?displayProperty=nameWithType>.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: testowanie równości odwołań (tożsamości)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|Opisuje sposób określenia, czy dwie zmienne mają równości odwołań.|  
|[Porady: Definiowanie równości wartości dla typu](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|Opisuje sposób zawierają niestandardowe definicje równości wartości dla typu.|  
|[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)|Zawiera linki do szczegółowych informacji o ważnych funkcji języka C# i funkcje, które są dostępne dla C# za pomocą programu .NET Framework.|  
|[Typy](../../../csharp/programming-guide/types/index.md)|Zawiera informacje o systemie typów języka C# i linki do dodatkowych informacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)

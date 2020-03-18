---
title: Porównania równości — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: f09d9891f79eda44c428d5509e341a54ad3a3eee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157107"
---
# <a name="equality-comparisons-c-programming-guide"></a>Porównania równości (Przewodnik programowania C#)

Czasami konieczne jest porównanie dwóch wartości równości. W niektórych przypadkach testujesz *dla równości wartości*, znany również jako *równoważność*, co oznacza, że wartości, które są zawarte w dwóch zmiennych są równe. W innych przypadkach należy określić, czy dwie zmienne odnoszą się do tego samego obiektu źródłowego w pamięci. Ten typ równości jest nazywany *równością referencyjną*lub *tożsamością*. W tym temacie opisano te dwa rodzaje równości i zawiera łącza do innych tematów, aby uzyskać więcej informacji.  
  
## <a name="reference-equality"></a>Równość referencyjna

 Równość odwołania oznacza, że dwa odwołania do obiektów odnoszą się do tego samego obiektu źródłowego. Może to nastąpić za pomocą prostego przypisania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 W tym kodzie dwa obiekty są tworzone, ale po instrukcji przypisania oba odwołania odnoszą się do tego samego obiektu. W związku z tym mają równość referencyjną. Użyj <xref:System.Object.ReferenceEquals%2A> metody, aby ustalić, czy dwa odwołania odnoszą się do tego samego obiektu.  
  
Pojęcie równości odniesienia stosuje się tylko do typów odwołań. Obiekty typu wartości nie mogą mieć równości odwołań, ponieważ gdy wystąpienie typu wartości jest przypisane do zmiennej, jest wykonana kopia wartości. W związku z tym nigdy nie można mieć dwóch struktur bez pudełka, które odwołują się do tej samej lokalizacji w pamięci. Ponadto jeśli używasz <xref:System.Object.ReferenceEquals%2A> do porównania dwóch typów wartości, `false`wynik będzie zawsze , nawet jeśli wartości, które są zawarte w obiektach są identyczne. Dzieje się tak, ponieważ każda zmienna jest zapakowana w oddzielne wystąpienie obiektu. Aby uzyskać więcej informacji, zobacz [Jak przetestować równość referencyjną (Tożsamość)](./how-to-test-for-reference-equality-identity.md).

## <a name="value-equality"></a>Równość wartości

 Równość wartości oznacza, że dwa obiekty zawierają tę samą wartość lub wartości. W przypadku typów wartości pierwotnych, takich jak [int](../../language-reference/builtin-types/integral-numeric-types.md) lub [bool,](../../language-reference/builtin-types/bool.md)testy równości wartości są proste. Można użyć [==](../../language-reference/operators/equality-operators.md#equality-operator-) operatora, jak pokazano w poniższym przykładzie.  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.
if (b == a)
{  
    // The two integers are equal.  
}  
```  
  
 Dla większości innych typów testowanie równości wartości jest bardziej skomplikowane, ponieważ wymaga, aby zrozumieć, jak typ definiuje go. Dla klas i struktur, które mają wiele pól lub właściwości, równość wartości jest często zdefiniowana oznacza, że wszystkie pola lub właściwości mają tę samą wartość. Na przykład `Point` dwa obiekty mogą być zdefiniowane jako równoważne, jeśli pointA.X jest równa pointB.X i pointA.Y jest równa pointB.Y.  
  
Nie ma jednak wymogu, aby równoważność była oparta na wszystkich polach typu. Może być oparty na podzbiorze. Podczas porównywania typów, które nie są własne, należy upewnić się, aby zrozumieć, jak równoważność jest zdefiniowana dla tego typu. Aby uzyskać więcej informacji na temat definiowania równości wartości we własnych klasach i strukturach, zobacz [Jak zdefiniować równość wartości dla typu](./how-to-define-value-equality-for-a-type.md).
  
### <a name="value-equality-for-floating-point-values"></a>Równość wartości dla wartości zmiennoprzecinkowych

 Porównania równości wartości zmiennoprzecinkowych[(podwójne](../../language-reference/builtin-types/floating-point-numeric-types.md) i [float)](../../language-reference/builtin-types/floating-point-numeric-types.md)są problematyczne ze względu na niedokładność arytmetyki zmiennoprzecinkowej na komputerach binarnych. Aby uzyskać więcej informacji, zobacz <xref:System.Double?displayProperty=nameWithType>uwagi w temacie .  
  
## <a name="related-topics"></a>Powiązane tematy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Jak przetestować równość referencyjną (Tożsamość)](./how-to-test-for-reference-equality-identity.md)|Opisuje sposób ustalania, czy dwie zmienne mają równość odwołania.|  
|[Definiowanie równości wartości dla typu](./how-to-define-value-equality-for-a-type.md)|Opisuje sposób zapewnienia niestandardowej definicji równości wartości dla typu.|  
|[Przewodnik programowania języka C#](../index.md)|Zawiera łącza do szczegółowych informacji o ważnych funkcji języka języka Języka C# i funkcje, które są dostępne dla Języka C# za pośrednictwem .NET Framework.|  
|[Typy](../types/index.md)|Zawiera informacje o systemie typu C# i łącza do dodatkowych informacji.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)

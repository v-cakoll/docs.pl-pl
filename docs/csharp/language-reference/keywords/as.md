---
title: as (odwołanie w C#)
ms.date: 10/11/2018
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: d6c9d44ff22881e6e5e7a542e1df41bbf77b23d8
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "49122729"
---
# <a name="as-c-reference"></a>as (odwołanie w C#)
Możesz użyć `as` operator pod kątem niektórych typów konwersje między typami zgodne odwołanie lub [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md). Poniższy kod przedstawia przykład.  
  
[!code-csharp[csrefKeywordsOperator#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#1)]

Jak pokazano w przykładzie, należy porównać wynik `as` wyrażenie `null` do sprawdzenia, jeśli konwersja zakończy się pomyślnie. Począwszy od języka C# 7.0, można użyć [jest](is.md) wyrażenie zarówno do testowania, że konwersja powiedzie się i warunkowo przypisać zmiennej po pomyślnym zakończeniu konwersji. W wielu scenariuszach, jest bardziej zwięzłe niż przy użyciu `as` operatora. Aby uzyskać więcej informacji, zobacz [wpisz wzór](is.md#type) części [ `is` operator](is.md) artykułu.
  
## <a name="remarks"></a>Uwagi  
 `as` Operator przypomina operacji rzutowania. Jednakże, jeśli konwersja nie jest możliwe, `as` zwraca `null` zamiast zgłaszania wyjątku. Rozważmy następujący przykład:  
  
```csharp  
expression as type  
```  
  
 Kod jest odpowiednikiem następujące wyrażenie, chyba że `expression` zmienna jest oceniane tylko raz.  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 Należy pamiętać, że `as` operator wykonuje konwersje odwołań, konwersje dopuszcza wartości null i opakowywanie konwersji. `as` Operator nie może wykonywać inne konwersji, takie jak konwersje zdefiniowane przez użytkownika, które należy zamiast tego przeprowadzić za pomocą wyrażenia cast.  
  
## <a name="example"></a>Przykład  

[!code-csharp[csrefKeywordsOperator#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#2)]
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [jako operator](~/_csharplang/spec/expressions.md#the-as-operator) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
 
## <a name="see-also"></a>Zobacz też  
- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [is](../../../csharp/language-reference/keywords/is.md)  
- [?:, operator](../../../csharp/language-reference/operators/conditional-operator.md)  
- [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)

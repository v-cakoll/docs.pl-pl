---
title: 'Porady: użycie wyrażeń lambda w kwerendzie (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 7b9808e1f9bfca362a1cc97aa97d77482928cc68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328139"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Porady: użycie wyrażeń lambda w kwerendzie (Przewodnik programowania w języku C#)
Wyrażenia lambda nie należy używać bezpośrednio w składni zapytania, ale ich używać w wywołaniach metody i wyrażenia zapytania może zawierać wywołania metody. W rzeczywistości niektóre operacje zapytań może być wyrażona w składni metody. Aby uzyskać więcej informacji na temat różnic między składnia zapytania a składnia metody, zobacz [składnia zapytania a składnia metody w technologii LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak używać wyrażenia lambda w kwerendzie oparte na metodzie przy użyciu <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> — operator zapytań standardowa. Należy pamiętać, że <xref:System.Linq.Enumerable.Where%2A> metoda w tym przykładzie ma parametru wejściowego typu obiektu delegowanego <xref:System.Func%601> i ten delegat przyjmuje jako dane wejściowe typu integer i zwraca wartość logiczną. Wyrażenie lambda, może zostać przekonwertowany do tego obiektu delegowanego. Jeżeli [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zapytania używanego <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> metoda, typ parametru byłaby `Expression<Func<int,bool>>` , ale wyrażenie lambda będzie wyglądać dokładnie. Aby uzyskać więcej informacji na typ wyrażenia, zobacz <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak używać wyrażenia lambda w wywołaniu metody w wyrażeniu zapytania. Wyrażenie lambda jest konieczne ponieważ <xref:System.Linq.Enumerable.Sum%2A> — operator zapytań standard nie można wywołać za pomocą składni zapytań.  
  
 Zapytanie najpierw grupy studentów zgodnie z ich poziomu klasy zgodnie z definicją w `GradeLevel` wyliczenia. Następnie dla każdej grupy dodaje całkowita wyniki dla użytkowników. To wymaga dwóch `Sum` operacji. Wewnętrzny `Sum` oblicza łączny wynik dla użytkowników i zewnętrznego `Sum` śledzi bieżącą, łącznie dla wszystkich studentów w grupie.  
  
 [!code-csharp[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i Wklej metodę do `StudentClass` zamieszczono w [porady: zapytanie kolekcji obiektów](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) i wywołać go z `Main` — metoda.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Drzewa wyrażeń](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)

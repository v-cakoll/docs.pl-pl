---
title: 'Porady: użycie wyrażeń lambda w kwerendzie (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 1632466aaa29cb79f053bd3ac2ca42e8b03ea89c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506487"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Porady: użycie wyrażeń lambda w kwerendzie (Przewodnik programowania w języku C#)
Nie należy używać wyrażeń lambda, bezpośrednio w składni zapytań, ale należy ich używać w wywołaniach metod i wyrażenia zapytania może zawierać wywołania metody. W rzeczywistości niektórych operacji zapytań może być wyrażona w składni metody. Aby uzyskać więcej informacji na temat różnic między składnia zapytania a składnia metody, zobacz [składnia zapytania a składnia metody w technologii LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć wyrażenia lambda w kwerendzie oparte na metodzie, za pomocą <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standardowego operatora zapytania. Należy pamiętać, że <xref:System.Linq.Enumerable.Where%2A> metody w tym przykładzie ma parametr wejściowy typu delegata <xref:System.Func%601> i ten delegat przyjmuje liczbę całkowitą jako dane wejściowe i zwraca wartość logiczną. Wyrażenie lambda można przekonwertować na delegata. Gdyby to [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] Zapytanie używane <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> metody, byłoby typ parametru `Expression<Func<int,bool>>` , ale wyrażenia lambda będzie wyglądać dokładnie tak. Aby uzyskać więcej informacji na temat typów wyrażeń, zobacz <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć wyrażenia lambda w wywołaniu metody, wyrażenia zapytania. Wyrażenie lambda jest konieczne ponieważ <xref:System.Linq.Enumerable.Sum%2A> standardowego operatora zapytania nie może być wywoływana przy użyciu składni zapytań.  
  
 Zgodnie z definicją w zapytaniu najpierw grupy uczniów, zgodnie z ich poziomem klasy korporacyjnej `GradeLevel` wyliczenia. Następnie dla każdej grupy dodaje całkowita wyniki dla każdego ucznia. Wymaga to dwóch `Sum` operacji. Wewnętrzny `Sum` oblicza łączny wynik dla każdego ucznia i zewnętrzny `Sum` śledzi bieżącą, łączna liczba dla wszystkich studentów w grupie.  
  
 [!code-csharp[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i Wklej metodę do `StudentClass` , znajduje się w [porady: zapytanie kolekcji obiektów](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) i wywołać go z `Main` metody.  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Drzewa wyrażeń (C#)](../concepts/expression-trees/index.md)  

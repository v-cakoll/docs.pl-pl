---
title: Jak używać wyrażeń lambda w kwerendzie — Przewodnik po programowaniu c#
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 92bdbf842c5c30b2f32e06f622f3e08f3c7a878f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711964"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Jak używać wyrażeń lambda w kwerendzie (Przewodnik programowania C#)
Wyrażenia lambda nie są używane bezpośrednio w składni kwerendy, ale są używane w wywołaniach metod, a wyrażenia kwerend mogą zawierać wywołania metody. W rzeczywistości niektóre operacje kwerendy mogą być wyrażone tylko w składni metody. Aby uzyskać więcej informacji na temat różnicy między składnią kwerendy a składnią metody, zobacz [Składnia kwerend y i Składnia metody w pliku LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak używać wyrażenia lambda w <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> kwerendzie opartej na metodach przy użyciu standardowego operatora kwerendy. Należy zauważyć, że <xref:System.Linq.Enumerable.Where%2A> metoda w tym przykładzie ma <xref:System.Func%602> parametr wejściowy typu delegata i delegat przyjmuje liczbę całkowitą jako dane wejściowe i zwraca wartość logiczną. Wyrażenie lambda można przekonwertować na tego delegata. Gdyby to [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] była kwerenda, która użyła <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> metody, typ parametru `Expression<Func<int,bool>>` będzie, ale wyrażenie lambda będzie wyglądać dokładnie tak samo. Aby uzyskać więcej informacji na <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>temat typu Wyrażenie, zobacz .  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak używać wyrażenia lambda w wywołaniu metody wyrażenia kwerendy. Lambda jest konieczne, <xref:System.Linq.Enumerable.Sum%2A> ponieważ operator kwerendy standardowej nie można wywołać przy użyciu składni kwerendy.  
  
 Zapytanie najpierw grupuje uczniów zgodnie z ich poziomem `GradeLevel` oceny, zgodnie z definicją w wyliczeniu. Następnie dla każdej grupy dodaje łączne wyniki dla każdego ucznia. Wymaga to `Sum` dwóch operacji. Wewnętrzny `Sum` oblicza całkowity wynik dla każdego ucznia, a zewnętrzna `Sum` utrzymuje uruchomiony, łączna suma dla wszystkich uczniów w grupie.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i wklej metodę `StudentClass` do, która znajduje się w Query kolekcji [obiektów](../../linq/query-a-collection-of-objects.md) i wywołać go z `Main` metody.
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia Lambda](./lambda-expressions.md)
- [Drzewa wyrażeń (C#)](../concepts/expression-trees/index.md)

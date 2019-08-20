---
title: 'Instrukcje: Użycie wyrażeń lambda w przewodniku C# programowania zapytań'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: bb784528226c706417166025a2469ed9f72f9cc2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588665"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Instrukcje: Używanie wyrażeń lambda w kwerendzie (C# Przewodnik programowania)
Wyrażenia lambda nie są używane bezpośrednio w składni zapytania, ale są używane w wywołaniach metod, a wyrażenia zapytań mogą zawierać wywołania metody. W rzeczywistości niektóre operacje zapytań można wyrazić tylko w składni metody. Aby uzyskać więcej informacji o różnicach między składnią zapytania i składnią metody, zobacz [składnia zapytań i składnia metod w LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób użycia wyrażenia lambda w kwerendzie opartej na metodzie przy użyciu <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standardowego operatora zapytań. Należy zauważyć, <xref:System.Linq.Enumerable.Where%2A> że metoda w tym przykładzie ma parametr wejściowy typu <xref:System.Func%602> delegata i że delegat przyjmuje liczbę całkowitą jako dane wejściowe i zwraca wartość logiczną. Wyrażenie lambda można przekonwertować na tego delegata. Jeśli było [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] to zapytanie, które <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> używało metody, typem `Expression<Func<int,bool>>` parametru będzie, ale wyrażenie lambda będzie wyglądać dokładnie tak samo. Aby uzyskać więcej informacji na temat typu wyrażenia, <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>Zobacz.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób użycia wyrażenia lambda w wywołaniu metody wyrażenia zapytania. Lambda jest konieczne, ponieważ <xref:System.Linq.Enumerable.Sum%2A> standardowego operatora zapytania nie można wywołać przy użyciu składni zapytania.  
  
 Zapytanie najpierw grupuje uczniów zgodnie z ich poziomem klasy, zgodnie z definicją w `GradeLevel` wyliczeniu. Następnie dla każdej grupy dodaje wszystkie wyniki dla każdego ucznia. Wymaga to dwóch `Sum` operacji. Wewnętrzna `Sum` oblicza łączny wynik dla każdego ucznia, a zewnętrzny `Sum` utrzymuje uruchomiony, łączny łącznie dla wszystkich uczniów w grupie.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i wklej metodę do programu `StudentClass` , która jest pokazana w [temacie How to: Zbadaj kolekcję obiektów](../linq-query-expressions/how-to-query-a-collection-of-objects.md) i Wywołaj ją `Main` z metody.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia lambda](./lambda-expressions.md)
- [Drzewa wyrażeń (C#)](../concepts/expression-trees/index.md)

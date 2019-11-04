---
title: 'Instrukcje: użycie wyrażeń lambda w przewodniku C# programowania zapytań'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: e7e7da211599b5ce0263377ecaf25b404399ce9c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423166"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Porady: użycie wyrażeń lambda w kwerendzie (Przewodnik programowania w języku C#)
Wyrażenia lambda nie są używane bezpośrednio w składni zapytania, ale są używane w wywołaniach metod, a wyrażenia zapytań mogą zawierać wywołania metody. W rzeczywistości niektóre operacje zapytań można wyrazić tylko w składni metody. Aby uzyskać więcej informacji o różnicach między składnią zapytania i składnią metody, zobacz [składnia zapytań i składnia metod w LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób użycia wyrażenia lambda w kwerendzie opartej na metodzie przy użyciu standardowego operatora zapytania <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>. Należy zauważyć, że metoda <xref:System.Linq.Enumerable.Where%2A> w tym przykładzie ma parametr wejściowy typu delegata <xref:System.Func%602> i ten delegat Pobiera liczbę całkowitą jako dane wejściowe i zwraca wartość logiczną. Wyrażenie lambda można przekonwertować na tego delegata. Jeśli było to zapytanie [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], które używa metody <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>, typem parametru będzie `Expression<Func<int,bool>>`, ale wyrażenie lambda będzie wyglądać dokładnie tak samo. Aby uzyskać więcej informacji na temat typu wyrażenia, zobacz <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób użycia wyrażenia lambda w wywołaniu metody wyrażenia zapytania. Lambda jest konieczne, ponieważ nie można wywołać standardowego operatora zapytania <xref:System.Linq.Enumerable.Sum%2A> przy użyciu składni zapytania.  
  
 Zapytanie najpierw grupuje uczniów zgodnie z ich poziomem jakości, zgodnie z definicją w `GradeLevel` Wyliczenie. Następnie dla każdej grupy dodaje wszystkie wyniki dla każdego ucznia. Wymaga to dwóch `Sum` operacji. Wewnętrzny `Sum` oblicza łączny wynik dla każdego ucznia, a zewnętrzny `Sum` utrzymuje uruchomiony, łączny łącznie dla wszystkich uczniów w grupie.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i wklej metodę do `StudentClass`, która znajduje się w podanej w [instrukcje: zapytania kolekcji obiektów](../../linq/query-a-collection-of-objects.md) i Wywołaj ją z metody `Main`.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia lambda](./lambda-expressions.md)
- [Drzewa wyrażeń (C#)](../concepts/expression-trees/index.md)

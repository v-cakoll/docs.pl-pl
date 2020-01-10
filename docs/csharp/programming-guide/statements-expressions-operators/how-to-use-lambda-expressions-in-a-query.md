---
title: Jak używać wyrażeń lambda w przewodniku C# programowania zapytań
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 92bdbf842c5c30b2f32e06f622f3e08f3c7a878f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711964"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Jak używać wyrażeń lambda w kwerendzie (C# Przewodnik programowania)
Wyrażenia lambda nie są używane bezpośrednio w składni zapytania, ale są używane w wywołaniach metod, a wyrażenia zapytań mogą zawierać wywołania metody. W rzeczywistości niektóre operacje zapytań można wyrazić tylko w składni metody. Aby uzyskać więcej informacji o różnicach między składnią zapytania i składnią metody, zobacz [składnia zapytań i składnia metod w LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób użycia wyrażenia lambda w kwerendzie opartej na metodzie przy użyciu standardowego operatora zapytania <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType>. Należy zauważyć, że metoda <xref:System.Linq.Enumerable.Where%2A> w tym przykładzie ma parametr wejściowy typu delegata <xref:System.Func%602> i ten delegat Pobiera liczbę całkowitą jako dane wejściowe i zwraca wartość logiczną. Wyrażenie lambda można przekonwertować na tego delegata. Jeśli było to zapytanie [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], które używa metody <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>, typem parametru będzie `Expression<Func<int,bool>>`, ale wyrażenie lambda będzie wyglądać dokładnie tak samo. Aby uzyskać więcej informacji na temat typu wyrażenia, zobacz <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób użycia wyrażenia lambda w wywołaniu metody wyrażenia zapytania. Lambda jest konieczne, ponieważ nie można wywołać standardowego operatora zapytania <xref:System.Linq.Enumerable.Sum%2A> przy użyciu składni zapytania.  
  
 Zapytanie najpierw grupuje uczniów zgodnie z ich poziomem jakości, zgodnie z definicją w `GradeLevel` Wyliczenie. Następnie dla każdej grupy dodaje wszystkie wyniki dla każdego ucznia. Wymaga to dwóch `Sum` operacji. Wewnętrzny `Sum` oblicza łączny wynik dla każdego ucznia, a zewnętrzny `Sum` utrzymuje uruchomiony, łączny łącznie dla wszystkich uczniów w grupie.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i wklej metodę do `StudentClass`, która jest dostarczana w [kwerendzie kolekcji obiektów](../../linq/query-a-collection-of-objects.md) i Wywołaj ją z metody `Main`.
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia lambda](./lambda-expressions.md)
- [Drzewa wyrażeń (C#)](../concepts/expression-trees/index.md)

---
title: Zapytania w LINQ to DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: bf3e15527fb3b6979e9363810dbffc05f164715c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662096"
---
# <a name="queries-in-linq-to-dataset"></a>Zapytania w LINQ to DataSet
Zapytanie jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są zwykle wyrażane w specjalistycznym języku zapytań, takich jak SQL dla relacyjnych baz danych i XQuery dla XML. W związku z tym deweloperzy musieli nauczyć się nowego języka zapytań dla każdego typu źródła danych lub formatu danych, które są zapytania. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] oferuje prostszy i spójny model do pracy z danymi w różnych rodzajach formatów i źródeł danych. W [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania, zawsze pracujesz z programowania obiektów.  
  
 A [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania operacja obejmuje trzy czynności: uzyskać lub źródeł danych, Utwórz zapytanie i wykonać zapytanie.  
  
 Źródła danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> interfejs ogólny może być odpytywana za pomocą [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Wywoływanie <xref:System.Data.DataTableExtensions.AsEnumerable%2A> na <xref:System.Data.DataTable> zwraca obiekt, który implementuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejs, który służy jako źródło danych dla programu LINQ do zapytań zestawu danych.  
  
 W zapytaniu określasz dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytania można również określić, jak te informacje powinny można sortowane, grupowane i kształtowane przed zwróceniem. W [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], zapytanie jest przechowywana w zmiennej. Jeśli zapytanie zaprojektowano w celu zwrócenia sekwencji wartości, sama zmienna zapytania musi być typem wyliczenia. Ta zmienna zapytania nie podejmuje żadnych działań i nie zwraca żadnych danych; tylko przechowuje informacje o kwerendzie. Po utworzeniu zapytania należy wykonać to zapytanie, aby pobrać wszystkie dane.  
  
 W zapytaniu, która zwraca sekwencję liczb sama zmienna kwerendy nigdy nie przechowuje wyników kwerendy i przechowuje tylko polecenia kwerendy. Wykonanie zapytania jest odroczone do czasu zmienna zapytania jest powtarzana w `foreach` lub `For Each` pętli. Jest to nazywane *wykonanie odroczone*; oznacza to, że zapytanie trochę czasu, po kwerendy jest tworzony jest wykonywany. Oznacza to, można wykonać zapytania tak często, jak chcesz. Jest to przydatne, gdy na przykład masz bazę danych, która jest aktualizowana przez inne aplikacje. W aplikacji można utworzyć zapytanie, aby pobrać najnowsze informacje, a następnie wielokrotnie wykonywania zapytania, zwracając zaktualizowane informacje o każdym.  
  
 W przeciwieństwie do odroczonego zapytań, zwracające je sekvence hodnot zapytań, które zwracają wartości pojedynczego wystąpienia są wykonywane natychmiast. Oto kilka przykładów pojedynczych zapytań <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, i <xref:System.Linq.Enumerable.First%2A>. Działają one od razu, ponieważ wyniki zapytania są wymagane do obliczenia pojedynczego wyniku. Na przykład w celu obliczenia średniej wyników zapytania zapytanie musi zostać wykonana tak, aby funkcja uśredniania wprowadził pracować z danymi. Można również użyć <xref:System.Linq.Enumerable.ToList%2A> lub <xref:System.Linq.Enumerable.ToArray%2A> metod na podstawie kwerendy, aby wymusić natychmiastowe wykonanie zapytania, który nie generuje wartości pojedynczego wystąpienia. Te techniki, aby wymusić natychmiastowe wykonanie może być przydatne, gdy chcesz buforować wyniki zapytania.
  
## <a name="queries"></a>Kwerendy  
 Zapytań LINQ to DataSet może zostać sformułowane w dwóch różnych składni: składnia wyrażenia oraz składni zapytania oparte na metodzie zapytania.  
  
### <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Wyrażenia kwerendy są deklaratywne składnię. Ta składnia umożliwia deweloperom Pisanie zapytań w języku C# lub Visual Basic w formacie podobnym do bazy danych SQL. Za pomocą składni wyrażeń zapytania, możesz wykonać nawet złożone filtrowanie, porządkowanie i operacji grupowania na źródeł danych za pomocą minimalnej ilości kodu. Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../csharp/linq/index.md#query-expression-overview) i [podstawowe operacje zapytań (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).
  
 .NET Framework środowisko uruchomieniowe języka wspólnego (CLR) nie można odczytać składni wyrażeń zapytania, sam. W związku z tym, w czasie kompilacji wyrażeń zapytania są tłumaczone na coś, co środowisko CLR zrozumienie: wywołania metody. Metody te są nazywane *standardowych operatorów zapytań*. Jako deweloper istnieje możliwość wywołania je bezpośrednio przy użyciu składni metody zamiast przy użyciu składni zapytań. Aby uzyskać więcej informacji, zobacz [składnia zapytania a składnia metody w technologii LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Przegląd](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> do zwrócenia wszystkich wierszy z `Product` tabelę i wyświetlić nazwy produktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Składni zapytania oparte na metodzie  
 Inny sposób, aby sformułować LINQ do zapytań zestaw danych jest użycie zapytania oparte na metodzie. Składnia zapytania oparte na metodzie to sekwencja wywołań metody bezpośredniej [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] metod operatorów, przekazując wyrażenia lambda jako parametry. Aby uzyskać więcej informacji, zobacz [wyrażeń Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> do zwrócenia wszystkich wierszy z `Product` i wyświetlić nazwy produktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Tworzenie zapytań  
 Jak wspomniano wcześniej w tym temacie, sama zmienna kwerendy przechowuje tylko polecenia kwerendy podczas kwerendy zaprojektowano w celu zwrócenia sekwencji wartości. Jeśli zapytanie nie zawiera metody, która spowoduje natychmiastowe wykonanie, rzeczywiste wykonanie zapytania jest odroczone do czasu iteracji nad zmienną kwerendy w `foreach` lub `For Each` pętli. Wykonanie odroczone umożliwia wielu zapytań, które można połączyć lub zapytanie, aby zostać rozszerzony. Podczas rozszerzania zapytania zostanie zmodyfikowany w celu uwzględnienia nowych operacji i ostateczną wykonywania odzwierciedlają zmiany. W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty. Drugie zapytanie rozszerza pierwszy przy użyciu `Where` do zwrócenia wszystkich produktów o rozmiarze "L":  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Po zapytanie zostało wykonane, nie dodatkowe zapytania mogą być składane, a wszystkie kolejne kwerendy będzie używać w pamięci [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operatorów. Wykonywanie zapytania ma miejsce, gdy iteracji nad zmienną kwerendy w `foreach` lub `For Each` instrukcji, lub przez wywołanie do jednego z [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operatory konwersji, które powodują natychmiastowe wykonanie. Te operatory obejmują następujące elementy: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, i <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty, które są uporządkowane według ceny. <xref:System.Linq.Enumerable.ToArray%2A> Metoda jest używana do wymuszenia wykonanie zapytania bezpośredniego:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [Wykonywanie zapytania do zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Wprowadzenie do korzystania z LINQ w C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Wprowadzenie do LINQ w Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)

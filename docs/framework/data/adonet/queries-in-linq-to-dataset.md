---
title: Zapytania w LINQ do DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f41a55cce6834b58526c84d9a82fb38e10f46b42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="queries-in-linq-to-dataset"></a>Zapytania w LINQ do DataSet
Zapytanie jest wyrażenie, które pobiera dane ze źródła danych. Zapytania są zwykle zapisywane w język kwerendy specjalnych, takich jak SQL relacyjnych baz danych i XQuery dla formatu XML. W związku z tym deweloperzy było nauczyć się nowy język kwerendy dla każdego typu źródła danych lub format danych są zapytania. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]zapewnia prostszy, spójny model do pracy z danymi w różnych rodzajów źródeł danych i formaty. W [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytanie, należy zawsze działa z programowania obiektów.  
  
 A [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania operacja obejmuje trzy czynności: uzyskać źródła danych lub źródła, Utwórz zapytanie i wykonać zapytanie.  
  
 Źródła danych, które implementują <xref:System.Collections.Generic.IEnumerable%601> ogólnego interfejsu można wyszukiwać za pomocą [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Wywoływanie <xref:System.Data.DataTableExtensions.AsEnumerable%2A> na <xref:System.Data.DataTable> zwraca obiekt, który implementuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejs, który służy jako źródło danych dla [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania.  
  
 W zapytaniu możesz określić dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytania można również określić, jak te informacje sortowania, grupowane i w kształcie przed zwróceniem jest. W [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], zapytanie jest przechowywana w zmiennej. Jeśli zapytanie służy do zwracania sekwencję wartości, samej zmiennej zapytania musi być typem wyliczenia. Ta zmienna zapytania Brak działania i zwraca żadnych danych; tylko przechowuje informacje o kwerendzie. Po utworzeniu zapytania należy wykonać zapytania można pobrać żadnych danych.  
  
 W zapytaniu, która zwraca sekwencję wartości samej zmiennej zapytanie nigdy nie zawiera wyników zapytania i przechowuje dane tylko w poleceniach zapytań. Wykonanie kwerendy jest odłożona do zmiennej zapytania jest powtórzyć za pośrednictwem w `foreach` lub `For Each` pętli. Ta metoda jest wywoływana *odroczonego wykonania*; oznacza to, że zapytania pewien czas po zapytaniu jest tworzony jest wykonywany. Oznacza to, że można wykonać zapytania często ma być. Jest to przydatne, gdy na przykład istnieć bazy danych, która jest aktualizowana przez inne aplikacje. W aplikacji można utworzyć kwerendę, aby pobrać najnowsze informacje i wielokrotnie wykonać zapytanie, zwracając zaktualizowane informacje zawsze.  
  
 W przeciwieństwie do zapytań odroczonych, zwracające sekwencję wartości zapytań zwracających wartości pojedynczego wystąpienia są wykonywane natychmiast. Oto kilka przykładów pojedynczych zapytań <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, i <xref:System.Linq.Enumerable.First%2A>. Natychmiast je wykonać operacji, ponieważ wyniki zapytania są wymagane do obliczenia pojedynczego wyniku. Na przykład w celu obliczenia średniej wyniki zapytania zapytanie musi zostać wykonana, aby funkcja uśredniania ma wejściowych danych do pracy z. Można również użyć <xref:System.Linq.Enumerable.ToList%2A> lub <xref:System.Linq.Enumerable.ToArray%2A> metod na podstawie kwerendy, aby wymusić natychmiastowe wykonywania zapytania, które nie tworzy wartości pojedynczego wystąpienia. Te techniki, aby wymusić natychmiastowe wykonanie może być przydatne, gdy chcesz buforować wyniki zapytania. Aby uzyskać więcej informacji o wykonanie odroczone i bezpośrednie kwerendy, zobacz [wprowadzenie do LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).  
  
## <a name="queries"></a>Kwerendy  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]zapytania można sformułować w dwóch składnie: wyrażenie składnia zapytania i metody zapytań.  
  
### <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Wyrażenia zapytania są deklaratywne składnię. Ta składnia umożliwia deweloperom Pisanie zapytań w C# lub Visual Basic w formacie podobnym do bazy danych SQL. Przy użyciu składni wyrażeń zapytania, można wykonywać nawet złożone filtrowanie, kolejność i operacji grupowania na źródeł danych z minimalnym kodu. Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](http://msdn.microsoft.com/library/40638f19-fb46-4d26-a2d9-a383b48f5ed4) i [podstawowe operacje zapytań (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 Składnia wyrażeń jest nowego w języku C# 3.0 i [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)]. Jednak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] środowisko uruchomieniowe języka wspólnego (CLR) nie może odczytać sam składnia wyrażenia zapytania. W związku z tym podczas kompilacji wyrażenia zapytania są translacji obsługiwanym przez środowisko CLR: wywołania metody. Te metody są określane jako *standardowych operatorów zapytań*. Deweloper istnieje możliwość wywołania je bezpośrednio, używając składni metody zamiast za pomocą składni zapytań. Aby uzyskać więcej informacji, zobacz [składnia zapytania a składnia metody w technologii LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Aby uzyskać więcej informacji o sposobie używania standardowych operatorów zapytań, zobacz [NOT IN kompilacji: Przewodnik programowania w języku LINQ ogólne](http://msdn.microsoft.com/en-us/609c7a6b-cbdd-429d-99f3-78d13d3bc049).  
  
 W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> do zwracanie wszystkich wierszy z `Product` tabelę i wyświetlić nazwy produktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Składnia zapytań — metoda  
 Innym sposobem sformułować [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania jest za pomocą zapytań na podstawie metody. Składnia zapytania oparte na metodzie jest sekwencję wywołań metody bezpośredniego [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] metody operatora, przekazując wyrażenia lambda jako parametry. Aby uzyskać więcej informacji, zobacz [wyrażenia Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 W tym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> do zwracanie wszystkich wierszy z `Product` i wyświetlić nazwy produktu.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Tworzenie kwerend  
 Jak wspomniano wcześniej w tym temacie, samej zmiennej zapytania są przechowywane w poleceniach zapytań podczas projektowania zapytania do zwrócenia sekwencję wartości. Jeśli zapytanie nie zawiera metody, które spowodują wykonanie natychmiastowe, rzeczywistego wykonania zapytania została odroczona dopóki iteracja zmienną zapytania w `foreach` lub `For Each` pętli. Wykonanie odroczone umożliwia wielu zapytań, aby można było połączyć lub kwerendę, aby zostać rozszerzony. Po rozszerzeniu zapytania on jest modyfikowane w celu uwzględnienia nowych operacji, a wykonanie ostatecznego zostaną one zastosowane zmiany. W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty. Drugiego zapytania rozszerza pierwszy przy użyciu `Where` do zwrócenia wszystkich produktów o rozmiarze "L":  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Po wykonaniu zapytania, nie dodatkowych zapytań, które mogą być składane i wszystkie kolejne kwerendy będą używały pamięć w [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operatorów. Wykonywanie zapytania ma miejsce, gdy iteracja zmienną zapytania w `foreach` lub `For Each` instrukcji, lub przez wywołanie do jednego z [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operatory konwersji, które powodują natychmiastowego wykonania. Operatory te są następujące: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, i <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty uporządkowanych według cennika. <xref:System.Linq.Enumerable.ToArray%2A> Metody, można wymusić wykonywania zapytania bezpośredniego:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [Wykonywanie zapytania do zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Wprowadzenie do korzystania z LINQ w C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wprowadzenie do korzystania z LINQ w Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)

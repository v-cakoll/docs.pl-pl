---
title: Zapytania w LINQ to DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: f6677e894e09b41e1f406d6b6485abf4168b5d6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946257"
---
# <a name="queries-in-linq-to-dataset"></a>Zapytania w LINQ to DataSet
Zapytanie jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są zwykle wyrażane w wyspecjalizowanym języku zapytań, takim jak SQL dla relacyjnych baz danych i XQuery for XML. W związku z tym deweloperzy musieli poznać nowy język zapytań dla każdego typu źródła danych lub formatu danych, który wykonuje zapytanie. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]oferuje prostszy, spójny model służący do pracy z danymi w różnych rodzajach źródeł danych i formatach. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] W zapytaniu zawsze pracujesz z obiektami programowania.  
  
 Operacja [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytania składa się z trzech akcji: uzyskanie źródła danych lub źródeł, utworzenie zapytania i wykonanie zapytania.  
  
 <xref:System.Collections.Generic.IEnumerable%601> Do[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]źródeł danych, które implementują interfejs ogólny, można wykonywać zapytania. Wywołanie <xref:System.Data.DataTableExtensions.AsEnumerable%2A> <xref:System.Collections.Generic.IEnumerable%601> na zwraca obiekt, który implementuje interfejs generyczny, który służy jako źródło danych dla zapytań LINQ to DataSet. <xref:System.Data.DataTable>  
  
 W zapytaniu należy określić dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytanie może również określać, jak te informacje powinny być sortowane, grupowane i ukształtowane przed zwróceniem. W [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]programie zapytanie jest przechowywane w zmiennej. Jeśli zapytanie zostało zaprojektowane w celu zwrócenia sekwencji wartości, zmienna zapytania musi być typem wyliczalnym. Ta zmienna zapytania nie przyjmuje żadnej akcji i nie zwraca żadnych danych. przechowuje on tylko informacje o zapytaniu. Po utworzeniu zapytania należy wykonać to zapytanie w celu pobrania danych.  
  
 W zapytaniu zwracającym sekwencję wartości, sama zmienna zapytania nigdy nie przechowuje wyników zapytania i zapisuje tylko polecenia zapytania. Wykonywanie zapytania jest odroczone do momentu powtarzania zmiennej zapytania w `foreach` pętli lub. `For Each` Jest to nazywane *wykonywaniem odroczonym*; oznacza to, że wykonanie zapytania następuje po pewnym czasie po skonstruowaniu zapytania. Oznacza to, że można wykonać zapytanie tak często, jak chcesz. Jest to przydatne, jeśli na przykład masz bazę danych, która jest aktualizowana przez inne aplikacje. W aplikacji można utworzyć zapytanie w celu pobrania najnowszych informacji i wielokrotnego wykonania zapytania, zwracającego zaktualizowane informacje za każdym razem.  
  
 W przeciwieństwie do odroczonych zapytań, które zwracają sekwencję wartości, zapytania zwracające wartość singleton są wykonywane natychmiastowo. Przykładami pojedynczych zapytań <xref:System.Linq.Enumerable.Count%2A>są, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, i <xref:System.Linq.Enumerable.First%2A>. Te czynności są wykonywane natychmiast, ponieważ wyniki zapytania są wymagane do obliczenia pojedynczego wyniku. Na przykład, aby znaleźć średnią wyników zapytania, należy wykonać zapytanie, tak aby średnia funkcja ma dane wejściowe do pracy z. Można również użyć <xref:System.Linq.Enumerable.ToList%2A> metod lub <xref:System.Linq.Enumerable.ToArray%2A> w zapytaniu, aby wymusić natychmiastowe wykonanie zapytania, które nie produkuje pojedynczej wartości. Te techniki do wymuszenia natychmiastowego wykonania mogą być przydatne, gdy chcesz buforować wyniki zapytania.
  
## <a name="queries"></a>Kwerendy  
 Zapytania LINQ to DataSet mogą być formułowane w dwóch różnych składni: składni wyrażeń zapytania i składni zapytania opartego na metodzie.  
  
### <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Wyrażenia zapytań są deklaratywną składnią zapytań. Ta składnia umożliwia deweloperowi Pisanie zapytań w programie C# lub Visual Basic w formacie podobnym do bazy danych SQL. Używając składni wyrażeń zapytania, można wykonywać nawet złożone operacje filtrowania, porządkowania i grupowania dla źródeł danych o minimalnym kodzie. Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../csharp/linq/index.md#query-expression-overview) i [podstawowe operacje zapytań (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).
  
 .NET Framework środowiska uruchomieniowego języka wspólnego (CLR) nie może odczytać składni wyrażenia zapytania. W związku z tym w czasie kompilacji wyrażenia zapytania są tłumaczone na element, który jest rozpoznawany przez środowisko CLR: wywołania metody. Metody te są określane jako *standardowe operatory zapytań*. Deweloperem jest możliwość wywoływania ich bezpośrednio przy użyciu składni metody zamiast przy użyciu składni zapytania. Aby uzyskać więcej informacji, zobacz [składnia zapytań i składnia metod w LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Omówienie](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Poniższy przykład używa <xref:System.Linq.Enumerable.Select%2A> do zwracania wszystkich wierszy z `Product` tabeli i wyświetla nazwy produktów.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Składnia zapytania oparta na metodzie  
 Innym sposobem formułowania zapytań LINQ to DataSet jest użycie zapytań opartych na metodzie. Składnia zapytania oparta na metodzie jest sekwencją metod bezpośrednich wywołań [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] metod operatora, przekazując wyrażenia lambda jako parametry. Aby uzyskać więcej informacji, zobacz [wyrażenia lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Ten przykład używa <xref:System.Linq.Enumerable.Select%2A> do zwracania wszystkich wierszy z `Product` i wyświetla nazwy produktów.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Tworzenie zapytań  
 Jak wspomniano wcześniej w tym temacie, zmienna zapytania tylko zapisuje polecenia zapytania, gdy zapytanie zostało zaprojektowane w celu zwrócenia sekwencji wartości. Jeśli zapytanie nie zawiera metody, która spowoduje natychmiastowe wykonanie, rzeczywiste wykonanie zapytania zostanie odroczone do momentu iteracji względem zmiennej zapytania w `foreach` pętli lub. `For Each` Wykonanie odroczone umożliwia łączenie wielu zapytań lub rozszerzanie zapytania. Po rozszerzeniu zapytania zostanie ono zmodyfikowane w celu uwzględnienia nowych operacji, a wykonanie ostateczne będzie odzwierciedlać zmiany. W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty. Drugie zapytanie rozszerza pierwszy przy użyciu `Where` programu w celu zwrócenia wszystkich produktów o rozmiarze "L":  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Po wykonaniu zapytania żadne dodatkowe zapytania nie mogą być składane, a wszystkie kolejne zapytania będą używały operatorów w pamięci [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] . Wykonanie zapytania zostanie wykonane, gdy przejdziesz do iteracji zmiennej zapytania `foreach` w `For Each` instrukcji or lub przez [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] wywołanie jednego z operatorów konwersji, które powodują natychmiastowe wykonanie. Te operatory obejmują następujące elementy: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, i <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty uporządkowane według cennika. <xref:System.Linq.Enumerable.ToArray%2A> Metoda służy do wymuszenia natychmiastowego wykonania zapytania:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [Wykonywanie zapytania do zestawów danych](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Wprowadzenie ze składnikami LINQ w Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)

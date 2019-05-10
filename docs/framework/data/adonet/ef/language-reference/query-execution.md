---
title: Wykonywanie zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: ee63b6df4f99415e5d36f0717ff325d9fbabd9e3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641608"
---
# <a name="query-execution"></a>Wykonywanie zapytania
Po utworzeniu zapytania LINQ przez użytkownika jest konwertowany na drzewo poleceń. Drzewo poleceń jest reprezentacją kwerendę, która jest zgodna z platformą Entity Framework. Drzewo poleceń jest następnie wykonywane względem źródła danych. W czasie wykonywania zapytań wszystkie wyrażenia zapytań (oznacza to, że wszystkie składniki zapytanie) są oceniane, tych wyrażeń, które są używane w tym w wyniku materializacja.  
  
 W jakich wyrażenia kwerendy punktu są wykonywane mogą się różnić. Zapytania LINQ są wykonywane zawsze, gdy zmienna zapytania jest powtarzana, nie wtedy, gdy zmienna zapytania jest tworzona. Jest to nazywane *wykonanie odroczone*. Możesz też wymusić zapytanie w celu wykonania od razu, co jest przydatne do buforowania wyników zapytania. Jest to opisane w dalszej części tego tematu.  
  
 Po wykonaniu zapytaniu składnika LINQ to Entities niektóre wyrażenia w zapytaniu mogą być wykonywane na serwerze, a niektóre części może być wykonywane lokalnie na komputerze klienckim. Po stronie klienta wyniku obliczenia wyrażenia odbywa się przed wykonaniem kwerendy na serwerze. Jeśli wyrażenie jest obliczane na komputerze klienckim, zostanie zastąpiony wynikiem tej oceny wyrażenia w zapytaniu, a następnie wykonywania zapytania na serwerze. Ponieważ zapytania są wykonywane w źródle danych, konfigurację źródła danych zastępuje nieaktywności klienta. Na przykład Obsługa wartości null i wartości liczbowych dokładności zależą od ustawień serwera. Wszelkie wyjątki zgłoszone podczas wykonywania zapytania na serwerze są przekazywane bezpośrednio do klienta.  
 
> [!TIP]
> Podsumowanie wygodne operatorów zapytań w formacie tabeli, która pozwala na szybkie identyfikowanie zachowanie wykonania operatora, zobacz [klasyfikacji dla standardowych operatorów zapytań przez sposób wykonywania (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Wykonanie odroczone zapytanie  
 W zapytaniu, która zwraca sekwencję liczb sama zmienna kwerendy nigdy nie przechowuje wyników kwerendy i przechowuje tylko polecenia kwerendy. Wykonanie zapytania jest odroczone do czasu zmienna zapytania jest powtarzana w `foreach` lub `For Each` pętli. Jest to nazywane *wykonanie odroczone*; oznacza to, że zapytanie trochę czasu, po kwerendy jest tworzony jest wykonywany. Oznacza to, można wykonać zapytania tak często, jak chcesz. Jest to przydatne, gdy na przykład masz bazę danych, która jest aktualizowana przez inne aplikacje. W aplikacji można utworzyć zapytanie, aby pobrać najnowsze informacje, a następnie wielokrotnie wykonywania zapytania, zwracając zaktualizowane informacje o każdym.  
  
 Wykonanie odroczone umożliwia wielu zapytań, które można połączyć lub zapytanie, aby zostać rozszerzony. Podczas rozszerzania zapytania zostanie zmodyfikowany w celu uwzględnienia nowych operacji i ostateczną wykonywania odzwierciedlają zmiany. W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty. Drugie zapytanie rozszerza pierwszy przy użyciu `Where` do zwrócenia wszystkich produktów o rozmiarze "L":  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Po wykonaniu kwerendy wszystkie kolejne kwerendy użyje operatorów LINQ w pamięci. Iterowanie za pomocą instrukcji nad zmienną kwerendy `foreach` lub `For Each` instrukcji lub wywołując jedną konwersję LINQ operatory spowoduje natychmiastowe wykonanie. Te operatory konwersji obejmują następujące elementy: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, i <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Wykonywanie zapytania bezpośredniego  
 W przeciwieństwie do odroczonego wykonania zapytania, które tworzą sekwencję wartości zapytania, które zwracają wartości pojedynczego wystąpienia są wykonywane natychmiast. Oto kilka przykładów pojedynczych zapytań <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.First%2A>, i <xref:System.Linq.Enumerable.Max%2A>. Działają one od razu, ponieważ zapytanie musi wygenerować sekwencji do obliczenia pojedynczego wyniku. Możesz też wymusić natychmiastowe wykonanie. Jest to przydatne, gdy chcesz buforować wyniki zapytania. Aby wymusić natychmiastowe wykonanie zapytania, który nie generuje wartości pojedynczego wystąpienia, możesz wywołać <xref:System.Linq.Enumerable.ToList%2A> metody <xref:System.Linq.Enumerable.ToDictionary%2A> metody lub <xref:System.Linq.Enumerable.ToArray%2A> metody zapytania lub zmienna zapytania. W poniższym przykładzie użyto <xref:System.Linq.Enumerable.ToArray%2A> metodę, aby od razu oceny sekwencji do tablicy.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Można również wymusić wykonanie przez umieszczenie `foreach` lub `For Each` pętli natychmiast po wyrażeniu zapytania, ale przez wywołanie metody <xref:System.Linq.Enumerable.ToList%2A> lub <xref:System.Linq.Enumerable.ToArray%2A> buforować wszystkie dane w jednym obiekcie kolekcji.  
  
## <a name="store-execution"></a>Wykonanie Store  
 Ogólnie rzecz biorąc wyrażenia w składniku LINQ to Entities są oceniane na serwerze i nie można się spodziewać zachowanie wyrażenia do wykonania typowych semantykę środowiska uruchomieniowego (języka wspólnego CLR) języka, ale te źródła danych. Istnieją jednak wyjątki, np. gdy wyrażenie jest wykonywane na komputerze klienckim. Może to spowodować nieoczekiwane wyniki, na przykład w przypadku serwera i klienta w różnych strefach czasowych.  
  
 Niektóre wyrażenia w zapytaniu może być wykonywane na komputerze klienckim. Ogólnie rzecz biorąc większość wykonywania zapytania są spodziewane na serwerze. Oprócz metod wykonywane względem elementy zapytania mapowane na źródło danych są często wyrażeń zapytania, które mogą być wykonywane lokalnie. Wykonanie lokalne wyrażenia zapytania daje wartość, która może służyć w wykonywania zapytań lub konstrukcji wynik.  
  
 Niektóre operacje są wykonywane zawsze na kliencie, takich jak powiązania wartości sub wyrażeń, sub zapytania od zamknięcia, a materializacja obiektów do wyników zapytania. Net to powoduje, że nie można zaktualizować te elementy (na przykład wartości parametrów), podczas wykonywania. Typy anonimowe może być skonstruowany wbudowane w źródle danych, ale nie można zakładać, aby to zrobić. Wbudowane grupy można skonstruować w źródle danych, jak również, ale to nie należy przyjąć, że w każdym wystąpieniu. Ogólnie rzecz biorąc najlepiej nie należy czynić żadnych założeń dotyczących co to jest tworzony na serwerze.  
  
 W tej sekcji opisano scenariusze, w których wykonywany jest kod lokalnie na komputerze klienckim. Aby uzyskać więcej informacji na temat tego, jakie typy wyrażeń są wykonywane lokalnie, zobacz [wyrażenia w zapytaniach jednostek składnika LINQ to](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Literały i parametry  
 Zmienne lokalne, takie jak `orderID` zmiennej w poniższym przykładzie są obliczane na komputerze klienckim.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Parametry metody również są obliczane na komputerze klienckim. `orderID` Parametr przekazywany do `MethodParameterExample` metody poniżej znajduje się przykład.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Literały rzutowania na komputerze klienckim  
 Rzutowanie z `null` do CLR typu jest wykonywany na komputerze klienckim:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Rzutowanie na typ, takich jak dopuszczający wartości null <xref:System.Decimal>, jest wykonywany na komputerze klienckim:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Konstruktory dla literałów  
 Nowe typy CLR, które mogą być mapowane na typy modelu koncepcyjnego są wykonywane na komputerze klienckim:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Nowych tablic są również wykonywane na komputerze klienckim.  
  
## <a name="store-exceptions"></a>Wyjątki Store  
 Wszelkie błędy magazynu, które zostaną napotkane podczas wykonywania zapytania są przekazywane do klienta i są nie mapowane lub obsługi.  
  
## <a name="store-configuration"></a>Konfiguracja Store  
 Podczas wykonywania zapytania w sklepie, konfiguracja magazynu zastępuje wszystkie zachowania klienta, a semantyka magazynu są wyrażone dla wszystkich działań i wyrażeń. Może to spowodować różnicy w zachowaniu CLR i przechowywać wykonywania w obszarach, takich jak porównania wartości null, porządkowanie identyfikator GUID, dokładność i dokładność operacje dotyczące typów danych dokładne (takie jak punktu zmiennoprzecinkowego lub <xref:System.DateTime>), a ciąg operacje. Należy mieć to na uwadze, podczas sprawdzania wyników zapytania.  
  
 Na przykład poniżej przedstawiono niektóre różnice w zachowaniu między CLR i programu SQL Server:  
  
- Program SQL Server zamówień identyfikatorów GUID inaczej niż środowiska CLR.  
  
- Można także różnice w wyniku dokładności podczas pracy z typu dziesiętnego w programie SQL Server. Jest to ze względu na wymagania dokładności stałych typu dziesiętnego programu SQL Server. Na przykład średnia <xref:System.Decimal> wartości 0.0, od 0,0 do 1,0 jest 0.3333333333333333333333333333 w pamięci na komputerze klienckim, ale 0.333333 w magazynie (oparte na domyślną precyzję typu dziesiętnego programu SQL Server).  
  
- Niektóre operacje porównania ciągów są również obsługiwane inaczej w programie SQL Server niż w CLR. Zachowanie porównania ciągu zależy od ustawienia sortowania na serwerze.  
  
- Wywołania funkcji lub metody, gdy uwzględniona w zapytaniu składnika LINQ to Entities, są mapowane na funkcje canonical platformy Entity Framework, które są następnie przetłumaczony na język Transact-SQL i wykonywane w bazie danych programu SQL Server. Istnieją przypadki, gdy zachowanie tych funkcji zamapowanego następującej liczby etapów stwierdzono mogą się różnić od implementacji w bibliotek klas bazowych. Na przykład, wywołanie <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, i <xref:System.String.EndsWith%2A> zwróci metody z pustym ciągiem jako parametr `true` gdy wykonywane w CLR, ale zwróci `false` podczas wykonywania w programie SQL Server. <xref:System.String.EndsWith%2A> Metoda może również zwracać różne wyniki, ponieważ program SQL Server uwzględnia dwa ciągi jako równe, jeśli różnią się odstępu, środowisko CLR uważa musiały być równe. Jest to zilustrowane na poniższym przykładzie:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]

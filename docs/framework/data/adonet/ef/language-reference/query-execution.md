---
title: Wykonywanie zapytania
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
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: db246037c388408e5722582049cf7a2b902caa18
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="query-execution"></a>Wykonywanie zapytania
Po utworzeniu zapytania LINQ przez użytkownika, zostanie przekonwertowane na drzewo poleceń. Drzewo poleceń jest reprezentację kwerendę, która jest zgodna z programu Entity Framework. Drzewo poleceń jest następnie wykonywane względem źródła danych. Podczas wykonywania zapytania wszystkie wyrażenia zapytania (to znaczy, że wszystkie składniki zapytania) są oceniane pod tym tych wyrażeń, które są używane w wyniku materialization.  
  
 Na jakie punktu wyrażenia zapytania są wykonywane może się różnić. Zapytania LINQ są zawsze wykonywane, gdy zmienną zapytania jest iterowane, nie, po utworzeniu zmiennej zapytania. Ta metoda jest wywoływana *odroczonego wykonania*. Możesz też wymusić zapytanie w celu wykonania natychmiast, który jest przydatny do buforowania wyników zapytania. Jest to opisane w dalszej części tego tematu.  
  
 Podczas wykonywania zapytania składnika LINQ to Entities, niektóre wyrażenia w zapytaniu może być wykonywane na serwerze, a niektóre elementy mogą wykonać lokalnie na komputerze klienckim. Obliczenie wyrażenia po stronie klienta odbywa się przed wykonaniem zapytania na serwerze. Jeśli wyrażenie jest obliczane na kliencie, zastępuje wynik tej oceny wyrażenia w zapytaniu, a następnie wykonać zapytania na serwerze. Konfiguracja źródła danych, ponieważ zapytania są wykonywane w źródle danych, zastępowanie zachowanie określone w kliencie. Na przykład Obsługa wartości null i dokładność wartości liczbowych są zależne od ustawień serwera. Wszelkie wyjątki zgłaszane podczas wykonywania zapytania na serwerze są przekazywane bezpośrednio do klienta.  
  
## <a name="deferred-query-execution"></a>Wykonywanie zapytań odroczonych  
 W zapytaniu, która zwraca sekwencję wartości samej zmiennej zapytanie nigdy nie zawiera wyników zapytania i przechowuje dane tylko w poleceniach zapytań. Wykonanie kwerendy jest odłożona do zmiennej zapytania jest powtórzyć za pośrednictwem w `foreach` lub `For Each` pętli. Jest to nazywane *odroczonego wykonania*; oznacza to, że zapytania pewien czas po zapytaniu jest tworzony jest wykonywany. Oznacza to, że można wykonać zapytania często chcesz. Jest to przydatne, gdy na przykład istnieć bazy danych, która jest aktualizowana przez inne aplikacje. W aplikacji można utworzyć kwerendę, aby pobrać najnowsze informacje i wielokrotnie wykonać zapytanie, zwracając zaktualizowane informacje zawsze.  
  
 Wykonanie odroczone umożliwia wielu zapytań, aby można było połączyć lub kwerendę, aby zostać rozszerzony. Po rozszerzeniu zapytania on jest modyfikowane w celu uwzględnienia nowych operacji, a wykonanie ostatecznego zostaną one zastosowane zmiany. W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty. Drugiego zapytania rozszerza pierwszy przy użyciu `Where` do zwrócenia wszystkich produktów o rozmiarze "L":  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Po wykonaniu kwerendy wszystkie kolejne kwerendy będą używać operatorów LINQ w pamięci. Iterowanie po zmienną zapytania przy użyciu `foreach` lub `For Each` instrukcji lub wywołując jedną konwersję LINQ operatory spowoduje natychmiastowe wykonywania. Te operatory konwersji są następujące: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, i <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Wykonywanie zapytania bezpośredniego  
 W przeciwieństwie do odroczonego wykonania zapytania, które powodują powstanie sekwencja wartości zapytań zwracających wartości pojedynczego wystąpienia są wykonywane natychmiast. Oto kilka przykładów pojedynczych zapytań <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.First%2A>, i <xref:System.Linq.Enumerable.Max%2A>. Natychmiast je wykonać operacji, ponieważ zapytanie musi mieć sekwencji do obliczania wyniku pojedynczą. Możesz też wymusić natychmiastowe wykonywania. Jest to przydatne, gdy chcesz buforować wyniki zapytania. Aby wymusić natychmiastowe wykonywania zapytania, które nie tworzy wartości pojedynczego wystąpienia, należy wywołać <xref:System.Linq.Enumerable.ToList%2A> metody <xref:System.Linq.Enumerable.ToDictionary%2A> metody, lub <xref:System.Linq.Enumerable.ToArray%2A> metoda zapytania lub zmienną zapytania. W poniższym przykładzie użyto <xref:System.Linq.Enumerable.ToArray%2A> metodę, aby natychmiast ocenić sekwencji do tablicy.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Wykonanie można również wymusić, ustawiając `foreach` lub `For Each` pętli natychmiast po wyrażeniu kwerendy, ale przez wywołanie metody <xref:System.Linq.Enumerable.ToList%2A> lub <xref:System.Linq.Enumerable.ToArray%2A> buforowania wszystkie dane w obiekcie jednej kolekcji.  
  
## <a name="store-execution"></a>Wykonanie magazynu  
 Ogólnie rzecz biorąc wyrażenia w składniku LINQ to Entities są oceniane na serwerze i nie można się spodziewać zachowanie wyrażenia do wykonania typowych semantykę języka wspólnego (CLR), ale te źródła danych. Istnieją jednak wyjątki od tej reguły, takie jak kiedy wyrażenie jest wykonywane na kliencie. Może to spowodować nieoczekiwane wyniki, na przykład gdy serwera i klienta znajdują się w różnych strefach czasowych.  
  
 Niektóre wyrażenia w zapytaniu może być wykonywane na kliencie. Ogólnie rzecz biorąc wykonywanie większości zapytania powinien wystąpić na serwerze. Jako uzupełnienie metod wykonywane zapytania elementy mapowane do źródła danych są często wyrażenia w zapytaniu, które mogą być wykonywane lokalnie. Wykonanie lokalne wyrażenia zapytania daje wartość, która może służyć wykonywania zapytania lub konstrukcji wynik.  
  
 Niektóre operacje są zawsze wykonywane po stronie klienta, takich jak powiązania wartości, a element sub wyrażenia, sub zapytania z zamknięć i materialization obiektów do wyników zapytania. Net to powoduje, że te elementy (na przykład wartości parametrów) nie można zaktualizować podczas wykonywania. Typy anonimowe mogą być zbudowane wbudowany w źródle danych, ale nie należy przyjąć, że to zrobić. W źródle danych, a także można skonstruować grupowania tekście, ale to nie należy przyjąć, że w każdym wystąpieniu. Ogólnie rzecz biorąc najlepiej nie przyjmuje żadnych założeń dotyczących co to jest tworzony na serwerze.  
  
 W tej sekcji opisano scenariusze, w których wykonywany jest kod lokalnie na komputerze klienckim. Aby uzyskać więcej informacji o tym, które typy wyrażeń są wykonywane lokalnie, zobacz [wyrażenia w składniku LINQ to Entities zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Literały i parametry  
 Zmienne lokalne, takie jak `orderID` zmiennej w poniższym przykładzie są oceniane na kliencie.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Parametry metody również są oceniane na kliencie. `orderID` Przekazany parametr `MethodParameterExample` metody poniżej, znajduje się przykład.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Literały Rzutowanie na kliencie  
 Rzutowanie z `null` do CLR typu jest wykonywane na komputerze klienckim:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Rzutowanie na typ, takie jak wartości null <xref:System.Decimal>, jest wykonywane na komputerze klienckim:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Konstruktory literałów  
 Nowe typy CLR, które mogą być mapowane na typach modelu koncepcyjnego są wykonywane na komputerze klienckim:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Nowe tablice są również wykonywane na kliencie.  
  
## <a name="store-exceptions"></a>Wyjątki magazynu  
 Magazyn błędów napotkanych podczas wykonywania zapytania są przekazywane do klienta i są nie mapowany lub obsługi.  
  
## <a name="store-configuration"></a>Konfiguracja magazynu  
 Po wykonaniu zapytania w magazynie, konfiguracja magazynu zastępuje wszystkie zachowania klienta i semantyki magazynu są wyrażane dla wszystkich operacji i wyrażenia. Może to spowodować różnice w zachowaniu między CLR i przechowywać wykonywania w obszarach, takich jak porównania wartości null, kolejność identyfikator GUID, dokładność i dokładność operacji dotyczących typów danych ścisłym (takich jak zmiennoprzecinkową typy punktów lub <xref:System.DateTime>), a ciąg operacje. Należy pamiętać, to podczas sprawdzania wyników zapytania.  
  
 Na przykład poniżej przedstawiono niektóre różnice w zachowaniu między CLR i SQL Server:  
  
-   SQL Server zamówień identyfikatorów GUID inaczej niż środowiska CLR.  
  
-   Można także różnice w wyniku dokładności podczas pracy z typem Decimal na serwerze SQL. Jest to spowodowane wymagania dokładności stałej typu dziesiętnego programu SQL Server. Na przykład średnia <xref:System.Decimal> wartości 0.0, 0.0 i 1.0 jest 0.3333333333333333333333333333 w pamięci na komputerze klienckim, ale 0.333333 w magazynie (na podstawie domyślna dokładność dla typu decimal programu SQL Server).  
  
-   Niektóre operacje na ciągach porównania są również obsługiwane inaczej w programie SQL Server niż w środowisku CLR. Zachowanie porównanie ciągu zależy od ustawienia sortowania na serwerze.  
  
-   Funkcja lub metoda wywołania, gdy uwzględnione w zapytaniu składnika LINQ to Entities, są mapowane na kanonicznej funkcji programu Entity Framework, które są następnie przetłumaczony na język Transact-SQL i wykonać w bazie danych programu SQL Server. Istnieją przypadki, jeśli zachowanie tych funkcji mapowanej wykazują może się różnić od implementacji w bibliotekach klasy podstawowej. Na przykład wywołanie elementu <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, i <xref:System.String.EndsWith%2A> zwróci metody za pomocą ciągu pustego jako parametr `true` gdy wykonywane w środowisku CLR, ale zwraca `false` podczas wykonywania w programie SQL Server. <xref:System.String.EndsWith%2A> Metoda może zwracać również różne wyniki, ponieważ program SQL Server uwzględnia dwa ciągi jako takie same, jeśli tylko różnią się one w końcu spację, CLR uważa je, aby nie może być taki sam. Jest to zilustrowane na poniższym przykładzie:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]

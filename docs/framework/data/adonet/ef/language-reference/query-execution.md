---
title: Wykonywanie zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: e372744eea3eed7fc3f7ee9c8bbdd711c95b586e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149976"
---
# <a name="query-execution"></a>Wykonywanie zapytania
Po utworzeniu kwerendy LINQ przez użytkownika jest ona konwertowana na drzewo poleceń. Drzewo poleceń jest reprezentacją kwerendy, która jest zgodna z entity framework. Drzewo poleceń jest następnie wykonywane względem źródła danych. W czasie wykonywania kwerendy wszystkie wyrażenia kwerendy (czyli wszystkie składniki kwerendy) są oceniane, łącznie z wyrażeniami, które są używane w materializacji wyników.  
  
 W jakim momencie wykonywane są wyrażenia zapytania mogą się różnić. Zapytania LINQ są zawsze wykonywane, gdy zmienna kwerendy jest iterowana, a nie podczas tworzenia zmiennej kwerendy. Nazywa się to *odroczonym wykonaniem*. Można również wymusić kwerendę do wykonania natychmiast, co jest przydatne do buforowania wyników kwerendy. Jest to opisane w dalszej części tego tematu.  
  
 Podczas wykonywania kwerendy LINQ do jednostek, niektóre wyrażenia w kwerendzie mogą być wykonywane na serwerze, a niektóre części mogą być wykonywane lokalnie na kliencie. Ocena wyrażenia po stronie klienta odbywa się przed wykonaniem kwerendy na serwerze. Jeśli wyrażenie jest oceniane na kliencie, wynik tej oceny jest zastępowany wyrażeniem w kwerendzie, a następnie kwerenda jest wykonywana na serwerze. Ponieważ kwerendy są wykonywane w źródle danych, konfiguracja źródła danych zastępuje zachowanie określone w kliencie. Na przykład obsługa wartości null i dokładność numeryczna zależą od ustawień serwera. Wszelkie wyjątki zgłaszane podczas wykonywania kwerendy na serwerze są przekazywane bezpośrednio do klienta.  

> [!TIP]
> Aby uzyskać wygodne podsumowanie operatorów zapytań w formacie tabeli, które umożliwia szybkie identyfikowanie zachowania wykonywania operatora, zobacz [Klasyfikacja standardowych operatorów zapytań według sposobu wykonywania (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Odroczone wykonanie kwerendy  
 W kwerendzie, która zwraca sekwencję wartości, sama zmienna kwerendy nigdy nie przechowuje wyników kwerendy i przechowuje tylko polecenia kwerendy. Wykonanie kwerendy jest odroczone, dopóki zmienna kwerendy `foreach` `For Each` nie zostanie iterowana w pętli lub pętli. Jest to znane jako *odroczone wykonanie;* oznacza to, że wykonywanie kwerendy występuje jakiś czas po skonstruowaniu kwerendy. Oznacza to, że można wykonać kwerendę tak często, jak chcesz. Jest to przydatne, gdy na przykład masz bazę danych, która jest aktualizowana przez inne aplikacje. W aplikacji można utworzyć kwerendę, aby pobrać najnowsze informacje i wielokrotnie wykonać kwerendę, zwracając zaktualizowane informacje za każdym razem.  
  
 Odroczone wykonanie umożliwia połączenie wielu zapytań lub rozszerzenie kwerendy. Po rozszerknięciu kwerendy jest modyfikowana w celu uwzględnienia nowych operacji, a ostateczne wykonanie będzie odzwierciedlać zmiany. W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty. Drugie zapytanie rozszerza pierwszy `Where` przy użyciu do zwrócenia wszystkich produktów o rozmiarze "L":  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Po wykonaniu kwerendy wszystkie kolejne kwerendy będą używać operatorów LINQ w pamięci. Iteracja za pośrednictwem zmiennej `foreach` `For Each` kwerendy przy użyciu lub instrukcji lub wywołanie jednego z operatorów konwersji LINQ spowoduje natychmiastowe wykonanie. Te operatory konwersji <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A>są <xref:System.Linq.Enumerable.ToLookup%2A>następujące: , , i <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
## <a name="immediate-query-execution"></a>Natychmiastowe wykonanie kwerendy  
 W przeciwieństwie do odroczonego wykonywania zapytań, które produkują sekwencję wartości, kwerendy, które zwracają wartość singleton są wykonywane natychmiast. Niektóre przykłady zapytań singleton <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.First%2A>są <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Max%2A>, , i . Te wykonać natychmiast, ponieważ kwerenda musi utworzyć sekwencję do obliczania wyniku singleton. Można również wymusić natychmiastowe wykonanie. Jest to przydatne, gdy chcesz buforować wyniki kwerendy. Aby wymusić natychmiastowe wykonanie kwerendy, która nie tworzy <xref:System.Linq.Enumerable.ToList%2A> wartości singleton, można wywołać metodę, <xref:System.Linq.Enumerable.ToDictionary%2A> metodę lub <xref:System.Linq.Enumerable.ToArray%2A> metodę na kwerendę lub zmienną kwerendy. W poniższym przykładzie <xref:System.Linq.Enumerable.ToArray%2A> użyto metody do natychmiastowej oceny sekwencji w tablicy.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Można również wymusić `foreach` wykonanie, `For Each` umieszczając lub pętli natychmiast po <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A> wyrażeniu kwerendy, ale wywołując lub buforować wszystkie dane w jednym obiekcie kolekcji.  
  
## <a name="store-execution"></a>Wykonanie sklepu  
 Ogólnie rzecz biorąc wyrażenia w LINQ do jednostek są oceniane na serwerze i zachowanie wyrażenia nie należy oczekiwać, aby wykonać semantyka wspólnego środowiska wykonawczego języka (CLR), ale te ze źródła danych. Istnieją wyjątki od tego, jednak, takich jak gdy wyrażenie jest wykonywane na kliencie. Może to spowodować nieoczekiwane wyniki, na przykład gdy serwer i klient znajdują się w różnych strefach czasowych.  
  
 Niektóre wyrażenia w kwerendzie mogą być wykonywane na kliencie. Ogólnie rzecz biorąc oczekuje się, że większość wykonywania kwerendy występuje na serwerze. Oprócz metod wykonywanych względem elementów kwerendy mapowanych do źródła danych często istnieją wyrażenia w kwerendzie, które mogą być wykonywane lokalnie. Lokalne wykonanie wyrażenia kwerendy daje wartość, która może być używana w wykonaniu kwerendy lub konstrukcji wynik.  
  
 Niektóre operacje są zawsze wykonywane na kliencie, takie jak powiązanie wartości, wyrażenia podrzędne, zapytania podrzędne z zamknięć i materializacja obiektów w wyniki kwerendy. Efekt netto jest to, że te elementy (na przykład wartości parametrów) nie można zaktualizować podczas wykonywania. Typy anonimowe mogą być konstruowane w linii w źródle danych, ale nie należy zakładać, aby to zrobić. Grupowania wbudowane mogą być konstruowane w źródle danych, jak również, ale nie należy zakładać w każdym wystąpieniu. Ogólnie rzecz biorąc, najlepiej nie zakładać, co jest skonstruowane na serwerze.  
  
 W tej sekcji opisano scenariusze, w których kod jest wykonywany lokalnie na kliencie. Aby uzyskać więcej informacji o typach wyrażeń wykonywanych lokalnie, zobacz [Wyrażenia w LINQ do zapytań jednostek](expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Literały i parametry  
 Zmienne lokalne, takie `orderID` jak zmienna w poniższym przykładzie, są oceniane na kliencie.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Parametry metody są również oceniane na kliencie. Parametr `orderID` przekazany do `MethodParameterExample` metody, poniżej, jest przykładem.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Casting Literały na klienta  
 Rzutowanie `null` z typu CLR jest wykonywane na kliencie:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Rzutowanie do typu, takiego <xref:System.Decimal>jak nullable , jest wykonywane na kliencie:  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Konstruktory do literałów  
 Nowe typy CLR, które mogą być mapowane na typy modeli koncepcyjnych są wykonywane na kliencie:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Nowe tablice są również wykonywane na kliencie.  
  
## <a name="store-exceptions"></a>Wyjątki sklepu  
 Wszelkie błędy magazynu, które występują podczas wykonywania kwerendy są przekazywane do klienta i nie są mapowane lub obsługiwane.  
  
## <a name="store-configuration"></a>Konfiguracja sklepu  
 Gdy kwerenda jest wykonywana w magazynie, konfiguracja magazynu zastępuje wszystkie zachowania klienta, a semantyka magazynu są wyrażone dla wszystkich operacji i wyrażeń. Może to spowodować różnicę w zachowaniu między CLR i wykonywania magazynu w obszarach, takich jak porównania null, kolejność identyfikatorów GUID, <xref:System.DateTime>dokładność i dokładność operacji obejmujących nieprecyzyjne typy danych (takich jak typy zmiennoprzecinkowe lub ) i operacji ciągów. Ważne jest, aby mieć to na uwadze podczas badania wyników kwerendy.  
  
 Na przykład poniżej przedstawiono pewne różnice w zachowaniu między programem CLR i SQL Server:  
  
- SQL Server zamawia identyfikatory GUID inaczej niż CLR.  
  
- Mogą również istnieć różnice w precyzji wyników w kontaktach z typem dziesiętnym na programie SQL Server. Wynika to ze stałych wymagań dotyczących precyzji typu dziesiętnego programu SQL Server. Na przykład średnia <xref:System.Decimal> wartości 0.0, 0.0 i 1.0 jest 0.3333333333333333333333333333333333 w pamięci na kliencie, ale 0.333333 w sklepie (na podstawie domyślnej precyzji dla typu dziesiętnego programu SQL Server).  
  
- Niektóre operacje porównywania ciągów są również obsługiwane inaczej w programie SQL Server niż w programie CLR. Zachowanie porównania ciągów zależy od ustawień sortowania na serwerze.  
  
- Wywołania funkcji lub metody, jeśli zawarte w LINQ do jednostki kwerendy, są mapowane do funkcji kanonicznych w entity framework, które są następnie tłumaczone na Transact-SQL i wykonywane w bazie danych programu SQL Server. Istnieją przypadki, gdy zachowanie tych mapowanych funkcji wykazują może różnić się od implementacji w bibliotekach klas podstawowych. Na <xref:System.String.Contains%2A>przykład wywołanie <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A> i metody z pustym `true` ciągiem jako parametr zwróci po `false` wykonaniu w programie CLR, ale zwróci po wykonaniu w programie SQL Server. Metoda <xref:System.String.EndsWith%2A> może również zwracać różne wyniki, ponieważ SQL Server uważa, że dwa ciągi są równe, jeśli różnią się tylko w końcowych odstępu, podczas gdy CLR uważa, że nie są równe. Ilustruje to poniższy przykład:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]

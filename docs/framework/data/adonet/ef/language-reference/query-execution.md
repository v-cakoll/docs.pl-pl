---
title: Wykonywanie zapytania
description: Poznaj różne sposoby uruchamiania zapytania LINQ to Entities, w tym odroczone wykonywanie zapytań, natychmiastowe wykonywanie zapytań i wykonywanie operacji zapisywania.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0e6cf23-63ac-47dd-bfe9-d5bdca826fac
ms.openlocfilehash: e776df6d35b6cc8c24cd83e902bc4d050347343b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286795"
---
# <a name="query-execution"></a>Wykonywanie zapytania
Po utworzeniu zapytania LINQ przez użytkownika zostanie ono przekonwertowane na drzewo poleceń. Drzewo poleceń jest reprezentacją zapytania, które jest zgodne z Entity Framework. Drzewo poleceń jest następnie wykonywane względem źródła danych. W czasie wykonywania zapytania są oceniane wszystkie wyrażenia zapytania (czyli wszystkie składniki zapytania), w tym te wyrażenia, które są używane w wyniku materializację.  
  
 Wskazuje, które wyrażenia zapytania są wykonywane, mogą się różnić. Zapytania LINQ są zawsze wykonywane, gdy zmienna zapytania jest powtarzana, a nie podczas tworzenia zmiennej zapytania. Jest to tzw. *wykonywanie odroczone*. Możesz też wymusić natychmiastowe wykonanie zapytania, co jest przydatne w przypadku buforowania wyników zapytania. Ten temat został opisany w dalszej części tego tematu.  
  
 Po wykonaniu zapytania LINQ to Entities niektóre wyrażenia w zapytaniu mogą być wykonywane na serwerze, a niektóre części mogą być wykonywane lokalnie na kliencie. Obliczanie po stronie klienta wyrażenia odbywa się przed wykonaniem zapytania na serwerze. Jeśli wyrażenie jest oceniane na kliencie, wynik tej oceny jest zastępowany dla wyrażenia w zapytaniu, a następnie jest wykonywane na serwerze. Ponieważ zapytania są wykonywane w źródle danych, konfiguracja źródła danych zastępuje zachowanie określone w kliencie. Na przykład obsługa wartości null i precyzja liczbowa zależą od ustawień serwera. Wszystkie wyjątki zgłoszone podczas wykonywania zapytania na serwerze są przesyłane bezpośrednio do klienta.  

> [!TIP]
> Aby uzyskać wygodne podsumowanie operatorów zapytań w formacie tabeli, która pozwala szybko określić zachowanie wykonywania operatora, zobacz [Klasyfikacja standardowych operatorów zapytań według sposobu wykonywania (C#)](../../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md).

## <a name="deferred-query-execution"></a>Wykonywanie odroczonego zapytania  
 W zapytaniu zwracającym sekwencję wartości, sama zmienna zapytania nigdy nie przechowuje wyników zapytania i zapisuje tylko polecenia zapytania. Wykonywanie zapytania jest odroczone do momentu powtarzania zmiennej zapytania w `foreach` `For Each` pętli lub. Jest to nazywane *wykonywaniem odroczonym*; oznacza to, że wykonanie zapytania następuje po pewnym czasie po skonstruowaniu zapytania. Oznacza to, że można wykonać zapytanie tak często, jak chcesz. Jest to przydatne, jeśli na przykład masz bazę danych, która jest aktualizowana przez inne aplikacje. W aplikacji można utworzyć zapytanie w celu pobrania najnowszych informacji i wielokrotnego wykonania zapytania, zwracającego zaktualizowane informacje za każdym razem.  
  
 Wykonanie odroczone umożliwia łączenie wielu zapytań lub rozszerzanie zapytania. Po rozszerzeniu zapytania zostanie ono zmodyfikowane w celu uwzględnienia nowych operacji, a wykonanie ostateczne będzie odzwierciedlać zmiany. W poniższym przykładzie pierwsze zapytanie zwraca wszystkie produkty. Drugie zapytanie rozszerza pierwszy przy użyciu programu `Where` w celu zwrócenia wszystkich produktów o rozmiarze "L":  
  
 [!code-csharp[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#composing1)]
 [!code-vb[DP L2E Conceptual Examples#Composing1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#composing1)]  
  
 Po wykonaniu zapytania wszystkie kolejne zapytania będą używały operatorów w pamięci LINQ. Iteracja względem zmiennej zapytania przy użyciu `foreach` instrukcji or `For Each` lub przez wywołanie jednego z operatorów konwersji LINQ spowoduje natychmiastowe wykonanie. Te operatory konwersji obejmują następujące elementy: <xref:System.Linq.Enumerable.ToList%2A> , <xref:System.Linq.Enumerable.ToArray%2A> , <xref:System.Linq.Enumerable.ToLookup%2A> , i <xref:System.Linq.Enumerable.ToDictionary%2A> .  
  
## <a name="immediate-query-execution"></a>Natychmiastowe wykonanie zapytania  
 W przeciwieństwie do odroczonego wykonania zapytań, które tworzą sekwencję wartości, zapytania, które zwracają wartość singleton, są wykonywane od razu. Przykładami pojedynczych zapytań są <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Count%2A> , <xref:System.Linq.Enumerable.First%2A> , i <xref:System.Linq.Enumerable.Max%2A> . Te metody są wykonywane natychmiast, ponieważ zapytanie musi utworzyć sekwencję, aby obliczyć pojedynczy wynik. Możesz również wymusić natychmiastowe wykonanie. Jest to przydatne, gdy chcesz buforować wyniki zapytania. Aby wymusić natychmiastowe wykonanie zapytania, które nie produkuje pojedynczej wartości, można wywołać <xref:System.Linq.Enumerable.ToList%2A> metodę, <xref:System.Linq.Enumerable.ToDictionary%2A> metodę lub <xref:System.Linq.Enumerable.ToArray%2A> metodę dla zapytania lub zmiennej zapytania. W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.ToArray%2A> metodę, aby natychmiast oszacować sekwencję do tablicy.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
 Możesz również wymusić wykonywanie przez umieszczenie `foreach` `For Each` pętli lub bezpośrednio po wyrażeniu zapytania, ale przez wywołanie <xref:System.Linq.Enumerable.ToList%2A> lub <xref:System.Linq.Enumerable.ToArray%2A> buforowanie wszystkich danych w jednym obiekcie kolekcji.  
  
## <a name="store-execution"></a>Wykonywanie magazynu  
 Ogólnie rzecz biorąc, wyrażenia w LINQ to Entities są oceniane na serwerze, a zachowanie wyrażenia nie powinno być oczekiwane przy użyciu semantyki środowiska uruchomieniowego języka wspólnego (CLR), ale te źródła danych. Istnieją między innymi wyjątki, na przykład gdy wyrażenie jest wykonywane na kliencie. Może to spowodować nieoczekiwane wyniki, na przykład wtedy, gdy serwer i klient znajdują się w różnych strefach czasowych.  
  
 Niektóre wyrażenia w zapytaniu mogą być wykonywane na kliencie. Ogólnie rzecz biorąc, większość wykonywania zapytań powinna wystąpić na serwerze. Poza metodami wykonywanymi względem elementów zapytania mapowanych na źródło danych w zapytaniu są często stosowane wyrażenia, które mogą być wykonywane lokalnie. Lokalne wykonanie wyrażenia zapytania zwraca wartość, której można użyć w konstrukcji wykonywania zapytania lub wyniku.  
  
 Niektóre operacje są zawsze wykonywane na kliencie, takie jak powiązanie wartości, podwyrażenia, podrzędne zapytania z zamknięć i materializację obiektów do wyników zapytania. Efektem netto tego elementu (na przykład wartości parametrów) nie można zaktualizować podczas wykonywania. Typy anonimowe mogą być zbudowane w tekście w źródle danych, ale nie powinny być zakładane w ten sposób. Wbudowane grupowania można utworzyć również w źródle danych, ale nie powinno się to zajmować w każdym wystąpieniu. Ogólnie rzecz biorąc, najlepiej nie należy wprowadzać żadnych założeń dotyczących tego, co jest zbudowane na serwerze.  
  
 W tej sekcji opisano scenariusze, w których kod jest wykonywany lokalnie na komputerze klienckim. Aby uzyskać więcej informacji na temat tego, które typy wyrażeń są wykonywane lokalnie, zobacz [wyrażenia w kwerendach LINQ to Entities](expressions-in-linq-to-entities-queries.md).  
  
### <a name="literals-and-parameters"></a>Literały i parametry  
 Zmienne lokalne, takie jak `orderID` zmienna w poniższym przykładzie, są oceniane na kliencie.  
  
 [!code-csharp[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#literalparameter1)]
 [!code-vb[DP L2E Conceptual Examples#LiteralParameter1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#literalparameter1)]  
  
 Parametry metody są również oceniane na kliencie. Parametr, który `orderID` został przesłany do `MethodParameterExample` metody, poniżej, jest przykładem.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodparameterexample)]
 [!code-vb[DP L2E Conceptual Examples#MethodParameterExample](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodparameterexample)]  
  
### <a name="casting-literals-on-the-client"></a>Rzutowanie literałów na kliencie  
 Rzutowanie z `null` na typ CLR jest wykonywane na kliencie:  
  
 [!code-csharp[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#nullcasttostring)]
 [!code-vb[DP L2E Conceptual Examples#NullCastToString](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#nullcasttostring)]  
  
 Na kliencie jest wykonywane rzutowanie na typ, na przykład na wartość null <xref:System.Decimal> :  
  
 [!code-csharp[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#casttonullable)]
 [!code-vb[DP L2E Conceptual Examples#CastToNullable](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#casttonullable)]  
  
### <a name="constructors-for-literals"></a>Konstruktory dla literałów  
 Nowe typy CLR, które mogą być mapowane na typy modelu koncepcyjnego, są wykonywane na kliencie:  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constructorforliteral)]
 [!code-vb[DP L2E Conceptual Examples#ConstructorForLiteral](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constructorforliteral)]  
  
 Nowe tablice są również wykonywane na kliencie.  
  
## <a name="store-exceptions"></a>Wyjątki magazynu  
 Wszystkie błędy magazynu, które są napotkane podczas wykonywania zapytania, są przesyłane do klienta i nie są zamapowane ani obsługiwane.  
  
## <a name="store-configuration"></a>Konfiguracja magazynu  
 Gdy zapytanie jest wykonywane w magazynie, Konfiguracja magazynu zastępuje wszystkie zachowania klienta, a semantyka magazynu jest wyrażana dla wszystkich operacji i wyrażeń. Może to skutkować różnicą między zachowaniem CLR a wykonaniem magazynu w obszarach takich jak porównania wartości null, porządkowanie identyfikatorów GUID, precyzja i dokładność operacji obejmujących nieprecyzyjne typy danych (takie jak zmiennoprzecinkowe typy lub <xref:System.DateTime> ) oraz operacje na ciągach. Ważne jest, aby pamiętać o tym podczas badania wyników zapytania.  
  
 Na przykład poniżej przedstawiono niektóre różnice w zachowaniu między środowiskiem CLR i SQL Server:  
  
- Identyfikatory GUID zamówień SQL Server różnią się od środowiska CLR.  
  
- W przypadku typu dziesiętnego w SQL Server mogą być również naliczane różnice dokładności wyników. Wynika to ze stałych wymagań dokładności SQL Server typu dziesiętnego. Na przykład średnia <xref:System.Decimal> wartość 0,0, 0,0 i 1,0 jest 0.3333333333333333333333333333 w pamięci na kliencie, ale 0,333333 w magazynie (na podstawie domyślnej dokładności dla typu dziesiętnego SQL Server).  
  
- Niektóre operacje porównywania ciągów są również obsługiwane inaczej w SQL Server niż w środowisku CLR. Zachowanie porównania ciągów zależy od ustawień sortowania na serwerze.  
  
- Wywołania funkcji lub metod, które znajdują się w zapytaniu LINQ to Entities, są mapowane na funkcje kanoniczne w Entity Framework, które następnie są tłumaczone na Transact-SQL i wykonywane w bazie danych SQL Server. Istnieją przypadki, gdy zachowanie tych mapowanych funkcji może różnić się od implementacji w bibliotekach klas bazowych. Na przykład wywoływanie <xref:System.String.Contains%2A> metod, <xref:System.String.StartsWith%2A> , i <xref:System.String.EndsWith%2A> z pustym ciągiem jako parametr zwróci wartość, `true` gdy zostanie wykonane w środowisku CLR, ale zwróci się `false` po wykonaniu w SQL Server. <xref:System.String.EndsWith%2A>Metoda może również zwracać różne wyniki, ponieważ SQL Server traktuje dwa ciągi, aby były równe, jeśli różnią się tylko znakami końcowymi, podczas gdy środowisko CLR uważa, że nie jest równe. Ilustruje to Poniższy przykład:  
  
 [!code-csharp[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#canonicalfuncvsclrbasetype)]
 [!code-vb[DP L2E Conceptual Examples#CanonicalFuncVsCLRBaseType](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#canonicalfuncvsclrbasetype)]

---
title: "Kształt drzew poleceń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c3311ac88355ac0d7214ec932719e1445757d9e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="the-shape-of-the-command-trees"></a>Kształt drzew poleceń
Moduł generowania SQL jest odpowiedzialny za wygenerowanie wewnętrznej bazy danych określonej kwerendy SQL na podstawie wyrażenia drzewa zapytanie wejściowe danego polecenia. W tej sekcji omówiono charakterystyki, właściwości i struktura drzewa polecenia zapytania.  
  
## <a name="query-command-trees-overview"></a>Przegląd drzewa polecenia zapytania  
 Drzewo poleceń zapytania jest reprezentacji modelu obiektu zapytania. Zapytanie drzewa polecenia służą dwa cele:  
  
-   Do wyrażenia zapytania określonego dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Do wyrażenia zapytania danych wyjściowych, znajduje się u dostawcy, który opisuje zapytanie wewnętrznej bazy danych.  
  
 Polecenie obsługę drzew bardziej rozbudowane semantyki niż SQL:1999 zgodne zapytania, łącznie z pomocy technicznej do pracy z zagnieżdżonych kolekcji i typ operacji, takich jak sprawdzanie, czy jednostka jest określonego typu lub Filtrowanie zestawów oparty na typie Query.  
  
 Właściwość DBQueryCommandTree.Query jest elementem głównym drzewa wyrażenia, który opisuje logiki kwerendy. Właściwość DBQueryCommandTree.Parameters zawiera listę parametrów, które są używane w zapytaniu. Drzewo wyrażenia składa się z obiektów DbExpression.  
  
 Obiekt DbExpression reprezentuje pewnych obliczeń. Kilka rodzajów wyrażenia są dostarczane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] do tworzenia wyrażenia zapytania, łącznie z stałe, zmienne, funkcje konstruktory i standardowe operatory, takie jak filtr i sprzężenia. Każdy obiekt DbExpression ma właściwość ResultType, który reprezentuje typ wyniku utworzone przez tego wyrażenia. Ten typ jest wyrażona jako właściwości TypeUsage.  
  
## <a name="shapes-of-the-output-query-command-tree"></a>Kształty drzewa dane wyjściowe polecenia zapytania  
 Drzew poleceń w danych wyjściowych zapytania ściśle reprezentują relacyjnego zapytania (SQL) i oparte na znacznie bardziej rygorystyczne zasady, niż te, które dotyczą drzew poleceń w kwerendzie. Zawierają one zazwyczaj konstrukcje, które są łatwe przetłumaczyć na język SQL.  
  
 Drzew poleceń w wejściowe są wyrażane w modelu koncepcyjnym, obsługująca właściwości nawigacji, skojarzenia między jednostkami i dziedziczenie. Dane wyjściowe polecenia drzew są wyrażane w modelu magazynu. Wprowadź drzew poleceń w umożliwiają projektu zagnieżdżonego kolekcji, ale nie drzew poleceń w danych wyjściowych.  
  
 Drzew poleceń w danych wyjściowych zapytania są tworzone przy użyciu podzbioru dostępnych obiektów DbExpression, a nawet niektóre wyrażenia w tym podzbiór ograniczono użycia.  
  
 Typ operacji, takich jak sprawdzanie, czy podane wyrażenie jest określonego typu lub filtrowanie na podstawie typu, zestawów nie występują w danych wyjściowych polecenia drzewa.  
  
 W danych wyjściowych polecenia drzewa tylko wyrażenia, które zwracają wartości logiczne są używane dla projekcje i tylko do predykatów w wyrażeniach wymagające predykatu filtru lub instrukcji case.  
  
 Katalog główny drzew poleceń w danych wyjściowych zapytania jest obiektem DbProjectExpression.  
  
### <a name="expression-types-not-present-in-output-query-command-trees"></a>Typy wyrażenia nie występują w drzew poleceń w danych wyjściowych zapytania  
 Następujące typy wyrażeń nie są prawidłowe w drzewie dane wyjściowe polecenia zapytania i nie muszą być obsługiwane przez dostawców:  
  
 Obiekt DbDerefExpression  
  
 Obiekt DbEntityRefExpression  
  
 Obiekt DbRefKeyExpression  
  
 DbIsOfExpression  
  
 DbOfTypeExpression  
  
 Obiekt DbRefExpression  
  
 DbRelationshipNavigationExpression  
  
 DbTreatExpression  
  
### <a name="expression-restrictions-and-notes"></a>Ograniczenia wyrażenia i uwagi  
 Wiele wyrażeń można używać tylko w sposób ograniczony w drzew poleceń w danych wyjściowych zapytania:  
  
#### <a name="dbfunctionexpression"></a>Obiekcie DbFunctionExpression  
 Można przekazać następujących funkcji:  
  
-   Canonical funkcje, które są rozpoznawane przez obszar nazw Edm.  
  
-   Funkcje wbudowane (magazyn), które są rozpoznawane przez BuiltInAttribute.  
  
-   Funkcje zdefiniowane przez użytkownika.  
  
 Canonical funkcji (zobacz [kanonicznej funkcji](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Aby uzyskać więcej informacji) są określone jako część [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], oraz dostawców należy dostarczyć implementacji dla funkcji kanonicznej na podstawie tych specyfikacji. Funkcje magazynu są oparte na specyfikacji w odpowiednich manifestu dostawcy. Funkcje zdefiniowane przez użytkownika są oparte na specyfikacji w pliku SSDL.  
  
 Ponadto funkcje, w których atrybut NiladicFunction nie mają argumentów i powinny być przekonwertowana bez nawiasów na końcu.  Oznacza to, do  *\<functionName >* zamiast  *\<functionName > ()*.  
  
#### <a name="dbnewinstanceexpression"></a>Obiekt DbNewInstanceExpression  
 Obiekt DbNewInstanceExpression może wystąpić tylko w następujących przypadków:  
  
-   Jako właściwość projekcji DbProjectExpression.  Zastosowanie następujące ograniczenia:  
  
    -   Typ wyniku musi być typu wiersz.  
  
    -   Każdy z argumentów jest wyrażenie zwraca wynik z typem pierwotnym. Zazwyczaj każdy argument jest wyrażenie skalarne, takie jak PropertyExpression nad DbVariableReferenceExpression, wywołania funkcji lub arytmetyczne obliczeń DbPropertyExpression za pośrednictwem DbVariableReferenceExpression lub wywołania funkcji . Jednak wyrażenie skalarne podzapytania reprezentujące może również wystąpić w liście argumentów dla obiekt DbNewInstanceExpression. Wyrażenie, które reprezentuje skalarne podzapytania jest reprezentujący podzapytania zwracające dokładnie jeden wiersz i jedną kolumnę typu pierwotnego z głównego obiektu DbElementExperession drzewa wyrażeń  
  
-   Z typem zwracanym kolekcji w którym to przypadku definiuje nową kolekcję wyrażeń podane jako argumenty.  
  
#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression  
 DbVariableReferenceExpression musi być elementem podrzędnym węzła DbPropertyExpression.  
  
#### <a name="dbgroupbyexpression"></a>DbGroupByExpression  
 Właściwość agregacji obiektu DbGroupByExpression może mieć tylko elementy typu DbFunctionAggregate. Nie ma żadnych innych typów agregacji.  
  
#### <a name="dblimitexpression"></a>DbLimitExpression  
 Właściwość limitu tylko może być obiektem DbConstantExpression lub DbParameterReferenceExpression. Również właściwość WithTies ma zawsze wartość false wersji programu .NET Framework w wersji 3.5 lub nowszej.  
  
#### <a name="dbscanexpression"></a>DbScanExpression  
 Gdy są używane w danych wyjściowych polecenia drzewa, DbScanExpression skutecznie reprezentuje skanowania przez tabelę, widok lub kwerendę magazynu reprezentowany przez EnitySetBase::Target.  
  
 Jeśli właściwość metadanych "Definiowanie zapytania" z elementem docelowym jest różna od null, reprezentuje zapytanie, tekst zapytania, dla której znajduje się w tej właściwości metadanych w dostawcy określonego języka (lub dialekt) określona w definicji schematu magazynu.  
  
 W przeciwnym razie element docelowy reprezentuje tabelę lub widok. Prefiksu jego schematu jest albo we właściwości metadanych "Schema", jeśli nie null, w przeciwnym razie jest nazwa kontenera jednostek.  Nazwa tabeli lub widoku jest albo właściwości metadanych "Table", jeśli nie wartość null, w przeciwnym razie podstawowej ustaw właściwość Name jednostki.  
  
 Te właściwości pochodzą z definicji odpowiednich obiektów EntitySet w pliku definicji schematu magazynu (SSDL).  
  
### <a name="using-primitive-types"></a>Używanie typów pierwotnych  
 W przypadku typów pierwotnych odwołuje się drzew poleceń w danych wyjściowych, są one zwykle przywoływany w typach pierwotnych modelu koncepcyjnego. Dla niektórych wyrażeń dostawców należy odpowiedni typ pierwotny magazynu. Przykłady takich wyrażeń obejmują DbCastExpression i prawdopodobnie DbNullExpression, jeśli dostawca wymaga można rzutować wartości null do odpowiedniego typu. W takich przypadkach dostawców należy wykonać mapowania na podstawie rodzaju typu pierwotnego i jego aspektów typ dostawcy.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)

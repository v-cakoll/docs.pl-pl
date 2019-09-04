---
title: Kształt drzew poleceń
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: a3568f3deeaeeb31b69b41ac7c767001b792a8eb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248222"
---
# <a name="the-shape-of-the-command-trees"></a>Kształt drzew poleceń

Moduł generowania kodu SQL jest odpowiedzialny za generowanie zapytania SQL specyficznego dla zaplecza na podstawie danego wyrażenia drzewa poleceń zapytania wejściowego. W tej sekcji omówiono właściwości, właściwości i strukturę drzew poleceń zapytania.

## <a name="query-command-trees-overview"></a>Omówienie drzew poleceń zapytania

Drzewo poleceń zapytania jest reprezentacją modelu obiektu zapytania. Drzewa poleceń zapytania mają dwa cele:

- Aby wyrazić zapytanie wejściowe, które jest określone względem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].

- Aby wyrazić zapytanie wyjściowe dostarczone dla dostawcy i opisuje zapytanie dotyczące zaplecza.

Drzewa poleceń zapytania obsługują bogatszą semantykę niż zapytania zgodne z językiem SQL: 1999, w tym obsługę pracy z kolekcjami zagnieżdżonymi i operacjami typu, takich jak sprawdzanie, czy jednostka jest określonego typu, lub filtrowanie zestawów na podstawie typu.

Właściwość DBQueryCommandTree. Query jest korzeniem drzewa wyrażenia opisującym logikę zapytania. Właściwość DBQueryCommandTree. Parameters zawiera listę parametrów, które są używane w zapytaniu. Drzewo wyrażenia składa się z obiektów DbExpression.

Obiekt DbExpression reprezentuje obliczanie. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Do tworzenia wyrażeń zapytań są dostarczane różne rodzaje wyrażeń, w tym stałe, zmienne, funkcje, konstruktory i standardowe operatory relacyjne, takie jak Filter i Join. Każdy obiekt DbExpression ma właściwość ResultType, która reprezentuje typ wyniku utworzonego przez to wyrażenie. Ten typ jest wyrażony jako TypeUsage.

## <a name="shapes-of-the-output-query-command-tree"></a>Kształty drzewa poleceń zapytania wyjściowego

Drzewa poleceń kwerendy wyjściowej ściśle reprezentują zapytania relacyjne (SQL) i przestrzegają wielu surowszych reguł niż te, które są stosowane do drzew poleceń zapytania. Zwykle zawierają konstrukcje, które można łatwo przetłumaczyć na SQL.

Drzewa poleceń wejściowych są wyrażane względem modelu koncepcyjnego, który obsługuje właściwości nawigacji, skojarzenia między jednostkami i dziedziczenie. Drzewa poleceń wyjściowych są wyrażane względem modelu magazynu. Drzewa poleceń wejściowych umożliwiają projektować kolekcje zagnieżdżone, ale nie są to drzewa poleceń wyjściowych.

Drzewa poleceń zapytania wyjściowego są kompilowane przy użyciu podzestawu dostępnych obiektów DbExpression, a nawet niektóre wyrażenia w tym podzbiorze mają ograniczone użycie.

Operacje typu, takie jak sprawdzanie, czy dane wyrażenie jest określonego typu lub zestawów filtrowania opartych na typie, nie są obecne w drzewach poleceń danych wyjściowych.

W drzewach poleceń wyjściowych tylko wyrażenia, które zwracają wartości logiczne, są używane dla projekcji i tylko dla predykatów w wyrażeniach wymagających predykatu, takiego jak filtr lub instrukcja Case.

Katalog główny drzew poleceń zapytania wyjściowego jest obiektem DbProjectExpression.

### <a name="expression-types-not-present-in-output-query-command-trees"></a>Typy wyrażeń nieobecne w drzewach poleceń zapytania wyjściowego

Następujące typy wyrażeń nie są prawidłowe w drzewie poleceń zapytania wyjściowego i nie muszą być obsługiwane przez dostawców:

- DbDerefExpression

- DbEntityRefExpression

- DbRefKeyExpression

- DbIsOfExpression

- DbOfTypeExpression

- DbRefExpression

- DbRelationshipNavigationExpression

- DbTreatExpression

### <a name="expression-restrictions-and-notes"></a>Ograniczenia i uwagi dotyczące wyrażeń

Wiele wyrażeń można używać tylko w ograniczony sposób w drzewach poleceń zapytania wyjściowego:

#### <a name="dbfunctionexpression"></a>DbFunctionExpression

Można przekazywać następujące typy funkcji:

- Funkcje kanoniczne, które są rozpoznawane przez przestrzeń nazw modelu EDM.

- Wbudowane funkcje (Store), które są rozpoznawane przez wbudowanego.

- Funkcje zdefiniowane przez użytkownika.

Funkcje kanoniczne (zobacz [funkcje kanoniczne](./language-reference/canonical-functions.md) [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], aby uzyskać więcej informacji) są określone jako część, a dostawcy powinni dostarczać implementacje dla funkcji kanonicznych na podstawie tych specyfikacji. Funkcje magazynu są oparte na specyfikacjach w odpowiednim manifeście dostawcy. Funkcje zdefiniowane przez użytkownika są oparte na specyfikacjach w SSDL.

Ponadto funkcje mające atrybut NiladicFunction nie mają argumentów i powinny być tłumaczone bez nawiasów na końcu.  Oznacza to, że do  *\<funkcji FunctionName*  *\<> zamiast FunctionName > ()* .

#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

Obiekt DbNewInstanceExpression może wystąpić tylko w następujących dwóch przypadkach:

- Jako właściwość projekcji elementu DbProjectExpression.  Gdy są stosowane następujące ograniczenia:

  - Typ wyniku musi być typem wiersza.

  - Każdy z argumentów jest wyrażeniem, które generuje wynik z typem pierwotnym. Zazwyczaj każdy argument jest wyrażeniem skalarnym, takim jak PropertyExpression na DbVariableReferenceExpression, wywołanie funkcji lub obliczenia arytmetyczne DbPropertyExpression za pośrednictwem DbVariableReferenceExpression lub wywołania funkcji . Jednak wyrażenie reprezentujące podzapytanie skalarne może również wystąpić na liście argumentów dla obiekt DbNewInstanceExpression. Wyrażenie reprezentujące podzapytanie skalarne jest drzewem wyrażenia, które reprezentuje podzapytanie, które zwraca dokładnie jeden wiersz i jedną kolumnę typu pierwotnego z DbElementExpression obiektem głównym

- Z typem zwracanym kolekcji, w tym przypadku definiuje nową kolekcję wyrażeń podanymi jako argumenty.

#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

DbVariableReferenceExpression musi być elementem podrzędnym węzła DbPropertyExpression.

#### <a name="dbgroupbyexpression"></a>DbGroupByExpression

Właściwość Aggregates elementu DbGroupAggregate może zawierać tylko elementy typu DbFunctionAggregate. Nie istnieją żadne inne typy agregacji.

#### <a name="dblimitexpression"></a>DbLimitExpression

Limitem właściwości może być tylko DbConstantExpression lub DbParameterReferenceExpression. Właściwość WithTies ma zawsze wartość false w wersji 3,5 .NET Framework.

#### <a name="dbscanexpression"></a>DbScanExpression

W przypadku użycia w drzewach poleceń wyjściowych DbScanExpression skutecznie reprezentuje skanowanie w tabeli, widoku lub zapytaniu magazynu reprezentowane przez EntitySetBase:: Target.

Jeśli właściwość metadanych "definiujące zapytanie" obiektu docelowego ma wartość różną od null, oznacza to, że jest to zapytanie, którego tekst zapytania znajduje się w tej właściwości metadanych w określonym języku (lub dialektie) dostawcy, jak określono w definicji schematu magazynu.

W przeciwnym razie element docelowy reprezentuje tabelę lub widok. Jego prefiks schematu znajduje się w właściwości metadanych "schemat", jeśli nie ma wartości null, w przeciwnym razie jest to nazwa kontenera jednostek.  Nazwa tabeli lub widoku to właściwość metadanych "Tabela", jeśli nie ma wartości null, w przeciwnym razie Właściwość Name bazy zestawu jednostek.

Wszystkie te właściwości pochodzą z definicji odpowiedniego obiektu EntitySet w pliku definicji schematu magazynu (SSDL).

### <a name="using-primitive-types"></a>Używanie typów pierwotnych

Gdy istnieją odwołania do typów pierwotnych w drzewach poleceń wyjściowych, są one zwykle przywoływane w typach pierwotnych modelu koncepcyjnego. Jednak w przypadku niektórych wyrażeń dostawcy potrzebują odpowiedniego typu pierwotnego magazynu. Przykłady takich wyrażeń to DbCastExpression i DbNullExpression, jeśli dostawca musi rzutować wartość null na odpowiedni typ. W takich przypadkach dostawcy powinni wykonać mapowanie do typu dostawcy na podstawie typu pierwotnego i jego aspektów.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL](sql-generation.md)

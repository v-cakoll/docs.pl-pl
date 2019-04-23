---
title: Kształt drzew poleceń
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 08a67c8d181188cbc14c6f60876a7e26cd6de25a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980086"
---
# <a name="the-shape-of-the-command-trees"></a>Kształt drzew poleceń

Moduł generowania SQL jest odpowiedzialny za wygenerowanie zapytania SQL określonych zaplecza opartego na wyrażenie kwerendy wejściowej danego polecenia drzewa. W tej sekcji omówiono cech, właściwości i struktury drzew poleceń zapytania.

## <a name="query-command-trees-overview"></a>Omówienie drzew poleceń zapytania

Drzewo poleceń zapytania jest reprezentacja obiektu modelu zapytania. Zapytanie drzew poleceń służą do dwóch celów:

- Wyrażenia kwerendy wejściowej, który jest określony względem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].

- Wyrażenia zapytań danych wyjściowych, znajduje się z dostawcą, który opisuje zapytanie do wewnętrznej bazy danych.

Wyślij zapytanie do polecenia drzewa obsługę semantyki bogatszy niż SQL:1999 kwerendy zgodne, w tym obsługę pracy z kolekcje zagnieżdżone oraz typ operacji, takich jak sprawdzanie, czy jednostka jest określonego typu lub filtrowanie na podstawie typu zestawów.

Właściwość DBQueryCommandTree.Query jest głównym drzewa wyrażeń, który opisuje logiki zapytania. Właściwość DBQueryCommandTree.Parameters zawiera listę parametrów, które są używane w zapytaniu. Drzewo wyrażenia składa się z obiektów DbExpression.

Obiekt DbExpression reprezentuje niektórych obliczeń. Kilka rodzajów wyrażenia są dostarczane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] do redagowania wyrażeń zapytania, łącznie ze stałymi, zmienne, funkcje, konstruktorów i standardowe operatory, takie jak filtrowanie i dołączania. Każdy obiekt DbExpression ma właściwość ResultType, który reprezentuje typ wynik tworzony przez to wyrażenie. Ten typ jest wyrażona jako właściwości TypeUsage.

## <a name="shapes-of-the-output-query-command-tree"></a>Kształty drzewo poleceń kwerendy danych wyjściowych

Drzew poleceń kwerendy danych wyjściowych ściśle reprezentują kwerend relacyjnych (SQL) i spełnić znacznie bardziej rygorystyczne zasady niż te, które dotyczą drzew poleceń zapytania. Zawierają one zazwyczaj konstrukcji, które łatwo są tłumaczone na SQL.

Drzew poleceń wejściowych są wyrażane względem modelu koncepcyjnego, która obsługuje właściwości nawigacji, skojarzenia między jednostkami i dziedziczenie. Dane wyjściowe polecenia drzewa są wyrażane w modelu magazynu. Wprowadź liczbę drzew poleceń umożliwiają projektu kolekcje zagnieżdżone, ale dane wyjściowe polecenia drzewa nie.

Drzew poleceń zapytania dane wyjściowe są tworzone za pomocą podzestawu dostępne obiekty DbExpression, a nawet niektóre wyrażenia, w tym podzbiór mają ograniczone użycie.

Typ operacji, takich jak sprawdzanie, czy podane wyrażenie jest określonego typu lub filtrowanie na podstawie typu, zestawy nie są obecne w danych wyjściowych drzew poleceń.

W danych wyjściowych polecenia drzewa tylko wyrażenia, które zwracają wartości logiczne są używane w przypadku projekcji i tylko w przypadku predykatów w wyrażeniach wymagające predykat filtru lub instrukcji case.

Główny drzew poleceń kwerendy danych wyjściowych jest obiektem DbProjectExpression.

### <a name="expression-types-not-present-in-output-query-command-trees"></a>Typy wyrażenia nieobecne w drzew poleceń kwerendy danych wyjściowych

Następujące typy wyrażeń nie są prawidłowe w drzewie polecenia kwerendy danych wyjściowych i nie muszą być obsługiwane przez dostawców:

- DbDerefExpression

- DbEntityRefExpression

- DbRefKeyExpression

- DbIsOfExpression

- DbOfTypeExpression

- DbRefExpression

- DbRelationshipNavigationExpression

- DbTreatExpression

### <a name="expression-restrictions-and-notes"></a>Wyrażenie ograniczenia i uwagi

Wiele wyrażeń należy używać tylko w sposób ograniczony w drzew poleceń kwerendy danych wyjściowych:

#### <a name="dbfunctionexpression"></a>DbFunctionExpression

Można przekazać następujących funkcji:

- Funkcje Canonical, które są rozpoznawane przez przestrzeń nazw Edm.

- Funkcje wbudowane (Sklep), które są rozpoznawane przez BuiltInAttribute.

- Funkcje zdefiniowane przez użytkownika.

Funkcje Canonical (zobacz [funkcje Canonical](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Aby uzyskać więcej informacji) są określane jako część [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], oraz dostawcy powinni dostarczać implementacje dla funkcji kanonicznej na podstawie tych specyfikacji. Funkcje Store są oparte na specyfikacji w odpowiedniej manifest dostawcy. Funkcje zdefiniowane przez użytkownika są oparte na specyfikacjach SSDL.

Ponadto funkcje, w których atrybut NiladicFunction ma nie argumentów i powinien być tłumaczony bez nawiasów, na końcu.  Oznacza to,  *\<functionName >* zamiast  *\<functionName > ()*.

#### <a name="dbnewinstanceexpression"></a>DbNewInstanceExpression

Obiekt DbNewInstanceExpression mogą występować tylko w dwóch przypadkach:

- Jako właściwość projekcji DbProjectExpression.  Gdy jest używana w związku z tym obowiązują następujące ograniczenia:

  - Typ wyniku musi być typu wiersza.

  - Każdy z jej argumentów jest wyrażeniem, który produkuje wynik z parametrem typu podstawowego. Zwykle każdy argument znajduje się wyrażenie skalarne, takie jak PropertyExpression nad DbVariableReferenceExpression, wywołania funkcji lub arytmetyczne obliczeń DbPropertyExpression DbVariableReferenceExpression lub wywołania funkcji . Jednak wyrażenie reprezentujące podzapytania skalarnej może również wystąpić na liście argumentów obiekt DbNewInstanceExpression. Wyrażenie, które reprezentuje skalarne podzapytania jest drzewo wyrażenia, reprezentujący podzapytania, która zwraca dokładnie jeden wiersz i jedną kolumnę typu prymitywnego za pomocą głównego obiektu DbElementExpression

- Z typem zwracanym kolekcji w którym to przypadku definiuje nową kolekcję wyrażeń dostarczone jako argumenty.

#### <a name="dbvariablereferenceexpression"></a>DbVariableReferenceExpression

DbVariableReferenceExpression musi być elementem podrzędnym węzła DbPropertyExpression.

#### <a name="dbgroupbyexpression"></a>DbGroupByExpression

Właściwość agregacje element dbgroupaggregate może zawierać tylko elementy typu DbFunctionAggregate. Istnieją inne typy agregacji.

#### <a name="dblimitexpression"></a>DbLimitExpression

Właściwość limitu tylko może być obiektem DbConstantExpression lub DbParameterReferenceExpression. Również właściwość WithTies jest zawsze wartość false, począwszy od programu .NET Framework w wersji 3.5.

#### <a name="dbscanexpression"></a>DbScanExpression

W przypadku użycia w danych wyjściowych drzew poleceń, DbScanExpression skutecznie reprezentuje skanowania za pośrednictwem tabeli, widoku lub zapytania magazynu, reprezentowane przez EntitySetBase::Target.

Jeśli właściwość metadanych "Definiowanie zapytania" element docelowy jest różna od null, reprezentuje zapytanie, tekst zapytania, dla której znajduje się w tej właściwości metadanych w dostawcy określonego języka (lub dialekt), jak to określono w definicji schematu magazynu.

W przeciwnym razie element docelowy reprezentuje tabelą ani widokiem. Jej prefiks schematu jest albo we właściwości metadanych "Schema", jeśli nie ma wartość null, w przeciwnym razie jest nazwa kontenera jednostki.  Nazwa tabeli lub widoku jest albo właściwość metadanych "Table", o ile nie wartość null, w przeciwnym razie podstawowego zestawu właściwości Name obiektu jednostki.

Te właściwości pochodzą z definicji odpowiedniego obiektu EntitySet w pliku definicji schematu magazynu (SSDL).

### <a name="using-primitive-types"></a>Przy użyciu typów pierwotnych

Gdy typy pierwotne są wywoływane w danych wyjściowych drzew poleceń, zwykle występuje do nich w typach pierwotnych modelu koncepcyjnego. Jednak niektóre wyrażenia dostawców na potrzeby odpowiedni typ pierwotny magazynu. Takie wyrażenia przykładami DbCastExpression i prawdopodobnie DbNullExpression, jeśli dostawca musi można rzutować wartości null do odpowiedniego typu. W takich przypadkach dostawców należy wykonać mapowanie na typ dostawcy, na podstawie typu pierwotnego typu i jego zestawów reguł.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)

---
title: "Szybkie odwołanie do jednostki SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 14d666624ac4572956364b3db3fd5ee7aad8799b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="entity-sql-quick-reference"></a>Szybkie odwołanie do jednostki SQL
Ten temat zawiera krótkie odwołanie do [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania. Zapytania w tym temacie są oparte na modelu AdventureWorks sprzedaży.  
  
## <a name="literals"></a>Literały  
  
### <a name="string"></a>String  
 Brak literałów ciągów znaków Unicode i z systemem innym niż Unicode. Ciągi Unicode są poprzedzony przez N. Na przykład `N'hello'`.  
  
 Poniżej przedstawiono przykład literału ciągu Non-Unicode:  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Cześć|  
  
### <a name="datetime"></a>DataGodzina  
 W literałach DateTime części zarówno data i godzina są obowiązkowe. Brak wartości domyślnej.  
  
 Przykład:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|12/25/2006 1:01:00: 00|  
  
### <a name="integer"></a>Liczba całkowita  
 Literały całkowite może być typu Int32 (123) UInt32 (123U), Int64 (123L) i UInt64 (123UL).  
  
 Przykład:  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>Inne  
 Inne literały obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są identyfikatora Guid, Binary, Float/Double, Decimal, i `null`. Pusty literał w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są uważane za zgodny z każdym innym typem w modelu koncepcyjnym.  
  
## <a name="type-constructors"></a>Konstruktory typu  
  
### <a name="row"></a>WIERSZ  
 [WIERSZ](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) tworzy anonimowe, strukturę wpisane wartości (rekordów) jak w:`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Przykład:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Dane wyjściowe:  
  
|Identyfikator produktu|Nazwa|  
|---------------|----------|  
|1|Regulowany wyścigu|  
|879|Uniwersalny roweru wstrzymania|  
|712|Logo AWC centralnych zasad dostępu|  
|...|...|  
  
### <a name="multiset"></a>ZESTAW WIELOKROTNY  
 [Zestaw WIELOKROTNY](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) tworzy kolekcje, takie jak:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Przykład:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Dane wyjściowe:  
  
|Identyfikator produktu|Nazwa|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Sakwy turystyczne, duże|PA T100|…|  
  
### <a name="object"></a>Obiekt  
 [O nazwie konstruktora typu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) tworzy (nazwane) obiekty zdefiniowane przez użytkownika, takie jak `person("abc", 12)`.  
  
 Przykład:  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Dane wyjściowe:  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|Identyfikator produktu|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Odwołania  
  
### <a name="ref"></a>REF  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki. Na przykład następujące zapytanie zwraca odwołania do każdej jednostki kolejności w zestawie jednostek zleceń:  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 W poniższym przykładzie użyto operatora wyodrębniania właściwości (.) do dostępu do właściwości jednostki. Gdy jest używany operator wyodrębniania właściwości, odwołanie jest automatycznie wyłuskiwany.  
  
 Przykład:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Regulowany wyścigu|  
|Uniwersalny roweru wstrzymania|  
|Logo AWC centralnych zasad dostępu|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) wyłuskań wartość odniesienia i daje w wyniku tego usunąć odwołania do. Na przykład następujące zapytanie generuje jednostek kolejności dla każdej kolejności w zestawie jednostek zamówień: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...  
  
 Przykład:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Regulowany wyścigu|  
|Uniwersalny roweru wstrzymania|  
|Logo AWC centralnych zasad dostępu|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF I KLUCZ  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) tworzy odwołanie przekazanie klucza. [KLUCZ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) wyodrębnia część klucza wyrażenie z typem odwołania.  
  
 Przykład:  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Identyfikator produktu|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>Funkcje  
  
### <a name="canonical"></a>Canonical  
 W obszarze nazw [kanonicznej funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) jest Edm, podobnie jak w `Edm.Length("string")`. Nie trzeba określać przestrzeń nazw, chyba że innej przestrzeni nazw jest importowany zawierającego funkcję z taką samą nazwę jak kanonicznej funkcji. Jeśli dwie przestrzenie nazw ma taką samą funkcję, użytkownik musi określonych pełną nazwę.  
  
 Przykład:  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Dane wyjściowe:  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Specyficzne dla dostawcy firmy Microsoft  
 [Funkcje właściwe dla dostawcy Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) w `SqlServer` przestrzeni nazw.  
  
 Przykład:  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Dane wyjściowe:  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Namespaces  
 [Przy użyciu](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) określa obszarów nazw używanych w wyrażeniu zapytania.  
  
 Przykład:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Stronicowania  
 Stronicowania można wyrazić za deklarowanie [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul do [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.  
  
 Przykład:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Dane wyjściowe:  
  
|ID|Nazwa|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Grupowanie  
 [Grupowanie według](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) Określa grupę, do których obiektów zwróconych przez kwerendę ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) zostaną umieszczone wyrażenia.  
  
 Przykład:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Dane wyjściowe:  
  
|nazwa|  
|----------|  
|Wszystki górski stanowisko zestawu|  
|ML górski stanowisko zestawu|  
|HL górski stanowisko zestawu|  
|...|  
  
## <a name="navigation"></a>Nawigacji  
 Operator nawigacji relacji umożliwia przejście przez relacji z jednego obiektu (od końca) do innej (Aby zakończyć). [Nawigacja](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) ma typ relacji kwalifikowany jako \<przestrzeń nazw >.\< Nazwa typu relacji >. Przejdź zwraca Ref\<T > Jeśli kardynalność na koniec jest 1. Jeśli kardynalność na koniec jest n, kolekcji < Ref\<T >> zostaną zwrócone.  
  
 Przykład:  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Dane wyjściowe:  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>WYBIERZ WARTOŚĆ I WYBIERZ POZYCJĘ  
  
### <a name="select-value"></a>WYBIERZ WARTOŚĆ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia w klauzuli SELECT VALUE pomijania konstrukcji niejawne wiersza. W klauzuli SELECT VALUE można określić tylko jeden element. Podczas takiej klauzuli jest używana, nie otoki wiersza jest tworzony wokół elementów w klauzuli SELECT i kolekcji żądanego kształtu można wyprodukować, na przykład: `SELECT VALUE a`.  
  
 Przykład:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Nazwa|  
|----------|  
|Regulowany wyścigu|  
|Uniwersalny roweru wstrzymania|  
|Logo AWC centralnych zasad dostępu|  
|...|  
  
### <a name="select"></a>WYBIERZ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia również Konstruktor row do utworzenia dowolnego wierszy. Wybierz przyjmuje jeden lub więcej elementów w projekcji i wyników w rekordzie danych z polami, na przykład: `SELECT a, b, c`.  
  
 Przykład:  
  
 Wybierz p.Name, p.ProductID z AdventureWorksEntities.Product jako dane wyjściowe p:  
  
|Nazwa|Identyfikator produktu|  
|----------|---------------|  
|Regulowany wyścigu|1|  
|Uniwersalny roweru wstrzymania|879|  
|Logo AWC centralnych zasad dostępu|712|  
|...|...|  
  
## <a name="case-expression"></a>WYRAŻENIE CASE  
 [Przypadek wyrażenie](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) ocenia zestaw wyrażeń logicznych w celu ustalenia wyniku.  
  
 Przykład:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|WARTOŚĆ TRUE|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

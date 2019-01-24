---
title: Szybkie odwołanie do jednostki SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 20d8d1cb1e4b5cbf37dffcce6a7e79c2a4c265d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539406"
---
# <a name="entity-sql-quick-reference"></a>Szybkie odwołanie do jednostki SQL
Ten temat zawiera krótki przewodnik po [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania. Zapytania w tym temacie są oparte na modelu sprzedaży AdventureWorks.  
  
## <a name="literals"></a>Literały  
  
### <a name="string"></a>String  
 Dostępne są literały ciągów znaków Unicode i innego niż Unicode. Ciągi Unicode są poprzedzonej ciągiem N. Na przykład `N'hello'`.  
  
 Oto przykład literału ciągu Unicode inne niż:  
  
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
 W literałach daty/godziny daty i godziny części są obowiązkowe. Brak wartości domyślnej.  
  
 Przykład:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|12/25/2006 1:01:00 AM|  
  
### <a name="integer"></a>Liczba całkowita  
 Literały całkowite mogą być typu Int32 (123) UInt32 (123U), Int64 (123L), a UInt64 (123UL).  
  
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
 Inne literały, obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to identyfikator Guid, pliku binarnego, Float/Double, Decimal, i `null`. Wartość null, literałów w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są uważane za zgodne z każdego innego typu w modelu koncepcyjnym.  
  
## <a name="type-constructors"></a>Konstruktorzy typów  
  
### <a name="row"></a>WIERSZ  
 [WIERSZ](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) tworzy anonimowe, strukturalnie wpisane (rekordów) wartością jako: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Przykład:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Dane wyjściowe:  
  
|Identyfikator produktu|Nazwa|  
|---------------|----------|  
|1|Wyścig zmienianych|  
|879|Uniwersalny roweru autonomicznej|  
|712|Czapka z Logo AWC|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) tworzy kolekcji, takie jak:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Przykład:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Dane wyjściowe:  
  
|Identyfikator produktu|Name (Nazwa)|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Sakwy turystyczne, duże|PA-T100|…|  
  
### <a name="object"></a>Obiekt  
 [O nazwie konstruktora typu](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) tworzy obiekty zdefiniowane przez użytkownika (o nazwie), takie jak `person("abc", 12)`.  
  
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
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki. Na przykład następujące zapytanie zwraca odwołania do każdej jednostki kolejność w zestawie jednostek zamówień:  
  
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
  
 W poniższym przykładzie użyto operatora wyodrębniania właściwości (.) do dostępu do właściwości jednostki. Gdy używany jest operator wyodrębniania właściwości, odwołanie jest automatycznie wyłuskiwany.  
  
 Przykład:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Wyścig zmienianych|  
|Uniwersalny roweru autonomicznej|  
|Czapka z Logo AWC|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) wyłuskań wartość odniesienia i generuje wyłuskania wynik tego obiektu. Na przykład, następujące zapytanie generuje jednostki zamówienia dla każdego zamówienia w zestawie jednostek zamówienia: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...  
  
 Przykład:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Wyścig zmienianych|  
|Uniwersalny roweru autonomicznej|  
|Czapka z Logo AWC|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF I KLUCZ  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) tworzy odwołanie przekazywania klucza. [KLUCZ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) wyodrębnia część klucza wyrażeniu zawierającym odwołania do typu.  
  
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
 Przestrzeń nazw dla [funkcje canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) jest Edm, podobnie jak w `Edm.Length("string")`. Nie masz Określ obszar nazw, chyba że innej przestrzeni nazw jest importowany zawierającego funkcję z taką samą nazwę jak kanonicznej funkcji. Jeśli dwie przestrzenie nazw mają taką samą funkcję, użytkownik musi określonych imię i nazwisko.  
  
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
  
### <a name="microsoft-provider-specific"></a>Microsoft Provider-Specific  
 [Funkcje właściwe dla dostawcy Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) znajdują się w `SqlServer` przestrzeni nazw.  
  
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
 [Za pomocą](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) Określa przestrzeń nazw używaną w wyrażeniu zapytania.  
  
 Przykład:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Stronicowania  
 Stronicowania może być wyrażona przez zadeklarowanie [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul do [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.  
  
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
 [Grupowanie według](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) określa grupy, do których obiektów zwróconych przez zapytanie ([wybierz](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) wyrażenie, które mają być umieszczone.  
  
 Przykład:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Dane wyjściowe:  
  
|nazwa|  
|----------|  
|LL górski stanowisko zestawu|  
|Uczenie Maszynowe górski stanowisko zestawu|  
|Rama górski stanowisko zestawu|  
|...|  
  
## <a name="navigation"></a>Nawigacja  
 Operator nawigacji relacji można przejść przez relacji z jednej jednostki (od końca) do innego (w celu zakończenia). [NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) przyjmuje odpowiednio wykwalifikowany typ relacji \<przestrzeni nazw >.\< Nazwa typu relacji >. Przejdź zwraca Ref\<T > Jeśli kardynalność do końca jest 1. Jeśli kardynalność do końca jest n, kolekcji < Ref\<T >> zostaną zwrócone.  
  
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
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] udostępnia klauzula SELECT VALUE, aby pominąć konstrukcji niejawne wiersza. Można określić tylko jeden element w klauzuli SELECT VALUE. Takie klauzula jest używana, nie otoki wiersza jest konstruowany wokół elementów w klauzuli SELECT, gdy kolekcja żądany kształt może wygenerować, na przykład: `SELECT VALUE a`.  
  
 Przykład:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Nazwa|  
|----------|  
|Wyścig zmienianych|  
|Uniwersalny roweru autonomicznej|  
|Czapka z Logo AWC|  
|...|  
  
### <a name="select"></a>WYBIERZ POZYCJĘ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapewnia także Konstruktor row do utworzenia dowolnego wierszy. Wybierz przyjmuje jeden lub więcej elementów w projekcji i wyniki w rekordzie danych z polami, na przykład: `SELECT a, b, c`.  
  
 Przykład:  
  
 Wybierz p.Name, p.ProductID z AdventureWorksEntities.Product jako dane wyjściowe p:  
  
|Nazwa|Identyfikator produktu|  
|----------|---------------|  
|Wyścig zmienianych|1|  
|Uniwersalny roweru autonomicznej|879|  
|Czapka z Logo AWC|712|  
|...|...|  
  
## <a name="case-expression"></a>WYRAŻENIE CASE  
 [Zamierzone, Zapisz wyrażenie](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) obliczenie zestawu wyrażeń logicznych w celu określenia wyniku.  
  
 Przykład:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|WARTOŚĆ TRUE|  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

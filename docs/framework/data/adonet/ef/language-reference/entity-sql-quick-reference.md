---
title: Szybkie odwołanie do języka Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7780359d981b130118cb73d4892f3dcb4b6e2e7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251028"
---
# <a name="entity-sql-quick-reference"></a>Szybkie odwołanie do języka Entity SQL
Ten temat zawiera krótkie informacje o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytaniach. Zapytania w tym temacie są oparte na modelu sprzedaży AdventureWorks.  
  
## <a name="literals"></a>Literały  
  
### <a name="string"></a>String  
 Istnieją literały ciągu Unicode i inne niż Unicode. Ciągi Unicode są poprzedzone znakiem N. Na przykład `N'hello'`.  
  
 Poniżej znajduje się przykład literału ciągu innego niż Unicode:  
  
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
 W literałach DateTime oba części daty i godziny są obowiązkowe. Brak wartości domyślnych.  
  
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
 Literały całkowite mogą być typu Int32 (123), UInt32 (123U), Int64 (123L) i UInt64 (123UL).  
  
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
 Inne literały obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] program to GUID, Binary, float/Double, Decimal i `null`. Literały o wartości [!INCLUDE[esql](../../../../../../includes/esql-md.md)] null w są uważane za zgodne z każdym innym typem w modelu koncepcyjnym.  
  
## <a name="type-constructors"></a>Konstruktory typów  
  
### <a name="row"></a>ROW  
 [Wiersz](row-entity-sql.md) konstruuje anonimową, strukturalnie wpisaną wartość w postaci:`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Przykład:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Dane wyjściowe:  
  
|Identyfikator produktu|Nazwa|  
|---------------|----------|  
|1|Wyścigi regulowane|  
|879|Podstawa roweru ogólnego przeznaczenia|  
|712|AWC logo|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 Kolekcje [zestawów wielokrotnych](multiset-entity-sql.md) , takie jak:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Przykład:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Dane wyjściowe:  
  
|Identyfikator produktu|Name (Nazwa)|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Obiekt  
 Konstrukcje [konstruktorów nazwanych](named-type-constructor-entity-sql.md) (o nazwach) obiekty zdefiniowane przez użytkownika `person("abc", 12)`, takie jak.  
  
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
 [Ref](ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki. Na przykład następujące zapytanie zwraca odwołania do każdej jednostki zamówienia w zestawie jednostek Orders:  
  
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
  
 Poniższy przykład używa operatora wyodrębniania właściwości (.) w celu uzyskania dostępu do właściwości jednostki. Gdy jest używany operator wyodrębniania właściwości, odwołanie jest automatycznie wywoływać.  
  
 Przykład:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Wyścigi regulowane|  
|Podstawa roweru ogólnego przeznaczenia|  
|AWC logo|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](deref-entity-sql.md) odwołuje się do wartości odniesienia i tworzy wynik tego odwołania. Na przykład następujące zapytanie tworzy jednostki Order dla każdego zamówienia w zestawie jednostek Orders: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..  
  
 Przykład:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Wyścigi regulowane|  
|Podstawa roweru ogólnego przeznaczenia|  
|AWC logo|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF I KLUCZ  
 [CreateRef](createref-entity-sql.md) tworzy odwołanie z przekazywaniem klucza. [Klucz](key-entity-sql.md) wyodrębnia część klucza wyrażenia z odwołaniem do typu.  
  
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
 Przestrzeń nazw dla [funkcji kanonicznych](canonical-functions.md) to EDM, jak `Edm.Length("string")`w. Nie trzeba określać przestrzeni nazw, chyba że zostanie zaimportowana inna przestrzeń nazw, która zawiera funkcję o takiej samej nazwie jak funkcja kanoniczna. Jeśli dwie przestrzenie nazw mają tę samą funkcję, użytkownik powinien mieć określoną pełną nazwę.  
  
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
 [Funkcje specyficzne dla dostawcy firmy Microsoft](../sqlclient-for-ef-functions.md) znajdują `SqlServer` się w przestrzeni nazw.  
  
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
 [Użycie](using-entity-sql.md) określa przestrzenie nazw używane w wyrażeniu zapytania.  
  
 Przykład:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Stronicowanie  
 Stronicowanie może być wyrażone za pomocą deklaracji podrzędnych klauzul [Skip](skip-entity-sql.md) i [Limit](limit-entity-sql.md) do klauzuli [order by](order-by-entity-sql.md) .  
  
 Przykład:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Dane wyjściowe:  
  
|id|Nazwa|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Grupowanie  
 [Grupowanie według](group-by-entity-sql.md) określa grupy, do których obiekty zwracane przez zapytanie ([SELECT](select-entity-sql.md)) mają zostać umieszczone.  
  
 Przykład:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Dane wyjściowe:  
  
|nazwa|  
|----------|  
|WSZYSTKO — zestaw stanowisk górskich|  
|Zestaw siedzeń górskich ML|  
|Zestaw miejsc górskich HL|  
|...|  
  
## <a name="navigation"></a>Nawigacja  
 Operator nawigacji relacji umożliwia nawigowanie po relacji od jednej jednostki (od końca) do innej (do końca). [Nawigacja](navigate-entity-sql.md) przyjmuje typ relacji kwalifikowana jako \<przestrzeń nazw >.\< Nazwa typu relacji >. Funkcja nawigacji zwraca\<wartość Ref T >, jeśli Kardynalność do końca jest równa 1. Jeśli Kardynalność do końca to n, zostanie zwrócona kolekcja < ref\<T > >.  
  
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
  
## <a name="select-value-and-select"></a>WYBIERZ POZYCJĘ WARTOŚĆ I WYBIERZ POZYCJĘ  
  
### <a name="select-value"></a>WYBIERZ WARTOŚĆ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia klauzulę SELECT VALUE, aby pominąć konstruowanie niejawnego wiersza. W klauzuli SELECT VALUE można określić tylko jeden element. Gdy taka klauzula jest używana, żadna otoka wiersza nie jest zbudowana wokół elementów w klauzuli SELECT i można utworzyć kolekcję żądanego kształtu, na przykład: `SELECT VALUE a`.  
  
 Przykład:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Dane wyjściowe:  
  
|Nazwa|  
|----------|  
|Wyścigi regulowane|  
|Podstawa roweru ogólnego przeznaczenia|  
|AWC logo|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia także konstruktora wierszy do konstruowania dowolnych wierszy. Zaznacz powoduje, że co najmniej jeden element w projekcji i wyniki w rekordzie danych z polami, na `SELECT a, b, c`przykład:.  
  
 Przykład:  
  
 Wybierz pozycję p.Name, p. ProductID z AdventureWorksEntities. Product jako p Output:  
  
|Nazwa|Identyfikator produktu|  
|----------|---------------|  
|Wyścigi regulowane|1|  
|Podstawa roweru ogólnego przeznaczenia|879|  
|AWC logo|712|  
|...|...|  
  
## <a name="case-expression"></a>WYRAŻENIE CASE  
 [Wyrażenie CASE](case-entity-sql.md) oblicza zestaw wyrażeń logicznych, aby określić wynik.  
  
 Przykład:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|OZNACZA|  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)

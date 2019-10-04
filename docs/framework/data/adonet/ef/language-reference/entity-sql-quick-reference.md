---
title: Szybkie odwołanie do języka Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 9ccfc461d394af8804c960ebf460e7fbfb025b64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833872"
---
# <a name="entity-sql-quick-reference"></a>Szybkie odwołanie do języka Entity SQL
Ten temat zawiera krótkie informacje o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytań. Zapytania w tym temacie są oparte na modelu sprzedaży AdventureWorks.  
  
## <a name="literals"></a>Literały  
  
### <a name="string"></a>String  
 Istnieją literały ciągu Unicode i inne niż Unicode. Ciągi Unicode są poprzedzone znakiem N. Na przykład `N'hello'`.  
  
 Poniżej znajduje się przykład literału ciągu innego niż Unicode:  
  
```sql  
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
  
```sql  
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
  
```sql  
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
 Inne literały obsługiwane przez [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to GUID, Binary, float/Double, Decimal i `null`. Literały null w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] są uważane za zgodne z każdym innym typem w modelu koncepcyjnym.  
  
## <a name="type-constructors"></a>Konstruktory typów  
  
### <a name="row"></a>ROW  
 [Wiersz](row-entity-sql.md) konstruuje anonimową, strukturalnie wpisaną wartość w postaci: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Przykład:  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 Dane wyjściowe:  
  
|Produktu|Nazwa|  
|---------------|----------|  
|1|Wyścigi regulowane|  
|879|Podstawa roweru ogólnego przeznaczenia|  
|712|AWC logo|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 Kolekcje [zestawów wielokrotnych](multiset-entity-sql.md) , takie jak:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Przykład:  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Dane wyjściowe:  
  
|Produktu|Nazwa|ProductNumber|...|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|...|  
  
### <a name="object"></a>Obiekt  
 Obiekty zdefiniowane przez użytkownika [(nazwane)](named-type-constructor-entity-sql.md) , takie jak `person("abc", 12)`.  
  
 Przykład:  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Dane wyjściowe:  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|Produktu|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Odwołania  
  
### <a name="ref"></a>REF  
 [Ref](ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki. Na przykład następujące zapytanie zwraca odwołania do każdej jednostki zamówienia w zestawie jednostek Orders:  
  
```sql  
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
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
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
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
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
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
```  
  
 Dane wyjściowe:  
  
|Produktu|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>Funkcje  
  
### <a name="canonical"></a>Postaci  
 Przestrzeń nazw dla [funkcji kanonicznych](canonical-functions.md) to EDM, jak w `Edm.Length("string")`. Nie trzeba określać przestrzeni nazw, chyba że zostanie zaimportowana inna przestrzeń nazw, która zawiera funkcję o takiej samej nazwie jak funkcja kanoniczna. Jeśli dwie przestrzenie nazw mają tę samą funkcję, użytkownik powinien mieć określoną pełną nazwę.  
  
 Przykład:  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
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
 [Funkcje specyficzne dla dostawcy firmy Microsoft](../sqlclient-for-ef-functions.md) znajdują się w przestrzeni nazw `SqlServer`.  
  
 Przykład:  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Dane wyjściowe:  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|25|  
  
## <a name="namespaces"></a>Namespaces  
 [Użycie](using-entity-sql.md) określa przestrzenie nazw używane w wyrażeniu zapytania.  
  
 Przykład:  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Stronicowanie  
 Stronicowanie może być wyrażone za pomocą deklaracji podrzędnych klauzul [Skip](skip-entity-sql.md) i [Limit](limit-entity-sql.md) do klauzuli [order by](order-by-entity-sql.md) .  
  
 Przykład:  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Dane wyjściowe:  
  
|ID|Nazwa|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Grupowanie  
 [Grupowanie według](group-by-entity-sql.md) określa grupy, do których obiekty zwracane przez zapytanie ([SELECT](select-entity-sql.md)) mają zostać umieszczone.  
  
 Przykład:  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
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
 Operator nawigacji relacji umożliwia nawigowanie po relacji od jednej jednostki (od końca) do innej (do końca). [Nawigowanie](navigate-entity-sql.md) przyjmuje typ relacji kwalifikowana jako \<namespace >. \<relationship typu >. Funkcja nawigacji zwraca wartość Ref @ no__t-0T >, jeśli Kardynalność do końca wynosi 1. Jeśli Kardynalność do końca to n, zostanie zwrócona kolekcja < ref @ no__t-0T > >.  
  
 Przykład:  
  
```sql  
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
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] udostępnia klauzulę SELECT VALUE, aby pominąć konstrukcję niejawnego wiersza. W klauzuli SELECT VALUE można określić tylko jeden element. Gdy taka klauzula jest używana, żadna otoka wiersza nie jest zbudowana wokół elementów w klauzuli SELECT i można utworzyć kolekcję żądanego kształtu, na przykład: `SELECT VALUE a`.  
  
 Przykład:  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 Dane wyjściowe:  
  
|Nazwa|  
|----------|  
|Wyścigi regulowane|  
|Podstawa roweru ogólnego przeznaczenia|  
|AWC logo|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] udostępnia także konstruktora wierszy do konstruowania dowolnych wierszy. Zaznacz powoduje, że co najmniej jeden element w projekcji i wyniki w rekordzie danych z polami, na przykład: `SELECT a, b, c`.  
  
 Przykład:  
  
 Wybierz pozycję p.Name, p. ProductID z AdventureWorksEntities. Product jako p Output:  
  
|Nazwa|Produktu|  
|----------|---------------|  
|Wyścigi regulowane|1|  
|Podstawa roweru ogólnego przeznaczenia|879|  
|AWC logo|712|  
|...|...|  
  
## <a name="case-expression"></a>WYRAŻENIE CASE  
 [Wyrażenie CASE](case-entity-sql.md) oblicza zestaw wyrażeń logicznych, aby określić wynik.  
  
 Przykład:  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|OZNACZA|  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)

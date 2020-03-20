---
title: Szybkie odwołanie do języka Entity SQL
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: fc7cf8f8f692f9dc4230569d5f575b6d5fad19fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150353"
---
# <a name="entity-sql-quick-reference"></a>Szybkie odwołanie do języka Entity SQL
Ten temat zawiera szybkie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] odwołanie do zapytań. Zapytania w tym temacie są oparte na modelu AdventureWorks Sales.  
  
## <a name="literals"></a>Literały  
  
### <a name="string"></a>Ciąg  
 Istnieją literały znaków Unicode i innych niż Unicode. Ciągi Unicode są poprzedzane z N. Na przykład `N'hello'`.  
  
 Poniżej przedstawiono przykład literału ciągu non-Unicode:  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 W datetime literały, zarówno daty i godziny części są obowiązkowe. Nie ma żadnych wartości domyślnych.  
  
 Przykład:  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|25.01.2006 1:01:00|  
  
### <a name="integer"></a>Liczba całkowita  
 Literały liczby całkowite mogą być typu Int32 (123), UInt32 (123U), Int64 (123L) i UInt64 (123UL).  
  
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
 Inne literały obsługiwane [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przez to Guid, Binary, Float/Double, `null`Decimal i . Literały null [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w są uważane za zgodne z każdym innym typem w modelu koncepcyjnym.  
  
## <a name="type-constructors"></a>Konstruktory typów  
  
### <a name="row"></a>ROW  
 [ROW](row-entity-sql.md) konstruuje wartość anonimową, typięcą strukturalną (rekord) jak w:`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Przykład:  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 Dane wyjściowe:  
  
|ProductID|Nazwa|  
|---------------|----------|  
|1|Regulowany wyścig|  
|879|Uniwersalny stojak rowerowy|  
|712|Czapka z logo AWC|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](multiset-entity-sql.md) tworzy kolekcje, takie jak:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Przykład:  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Dane wyjściowe:  
  
|ProductID|Nazwa|Productnumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Duży|Pa-T100|…|  
  
### <a name="object"></a>Obiekt  
 [Nazwane konstrukcje konstruktora](named-type-constructor-entity-sql.md) typu (nazwane) obiekty zdefiniowane przez użytkownika, takie jak `person("abc", 12)`.  
  
 Przykład:  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 Dane wyjściowe:  
  
|SalesOrderDetailID|Numer śledzenia przewoźnika|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Dokumentacja  
  
### <a name="ref"></a>REF  
 [REF](ref-entity-sql.md) tworzy odwołanie do wystąpienia typu jednostki. Na przykład następująca kwerenda zwraca odwołania do każdej encji Zamówienia w zestawie jednostek Zamówienia:  
  
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
  
 W poniższym przykładzie użyto operatora wyodrębniania właściwości (.) w celu uzyskania dostępu do właściwości jednostki. Gdy operator wyodrębniania właściwości jest używany, odwołanie jest automatycznie wyłuskiwane.  
  
 Przykład:  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Regulowany wyścig|  
|Uniwersalny stojak rowerowy|  
|Czapka z logo AWC|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](deref-entity-sql.md) wyłudzenie wartości referencyjnej i tworzy wynik tego wyłuskania. Na przykład następująca kwerenda tworzy Order jednostek dla każdego `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`Zamówienia w zestaw jednostek Zamówienia: ..  
  
 Przykład:  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Regulowany wyścig|  
|Uniwersalny stojak rowerowy|  
|Czapka z logo AWC|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF I KLUCZ  
 [CREATEREF](createref-entity-sql.md) tworzy odwołanie przekazując klucz. [KEY](key-entity-sql.md) wyodrębnia kluczową część wyrażenia z odwołaniem do typu.  
  
 Przykład:  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 Dane wyjściowe:  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>Funkcje  
  
### <a name="canonical"></a>Canonical  
 Obszar nazw dla [funkcji kanonicznych](canonical-functions.md) jest Edm, jak w `Edm.Length("string")`. Nie trzeba określać obszaru nazw, chyba że zostanie zaimportowana inna przestrzeń nazw zawierająca funkcję o takiej samej nazwie jak funkcja kanoniczna. Jeśli dwie przestrzenie nazw mają tę samą funkcję, użytkownik powinien podać pełną nazwę.  
  
 Przykład:  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Dane wyjściowe:  
  
|NazwaLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Specyficzne dla dostawcy firmy Microsoft  
 [Funkcje specyficzne dla](../sqlclient-for-ef-functions.md) dostawcy `SqlServer` firmy Microsoft znajdują się w obszarze nazw.  
  
 Przykład:  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Dane wyjściowe:  
  
|Wyślij wiadomość e-mailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Przestrzenie nazw  
 [USING](using-entity-sql.md) określa obszary nazw używane w wyrażeniu kwerendy.  
  
 Przykład:  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Stronicowanie  
 Stronicowanie może być wyrażone przez zadeklarowanie [skip](skip-entity-sql.md) i [limit](limit-entity-sql.md) podpunktów do [ORDER BY](order-by-entity-sql.md) klauzuli.  
  
 Przykład:  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Dane wyjściowe:  
  
|ID|Nazwa|  
|--------|----------|  
|10|Adina|  
|11|Okręg wyborczy Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Grupowanie  
 [POLECENIE GRUPOWANIE WEDŁUG](group-by-entity-sql.md) określa grupy, do których mają być umieszczone obiekty zwracane przez wyrażenie kwerendy ([SELECT).](select-entity-sql.md)  
  
 Przykład:  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Dane wyjściowe:  
  
|name|  
|----------|  
|LL Zgromadzenie siedzeń górskich|  
|ML Zgromadzenie siedzeń górskich|  
|HL Montaż siedzenia górskiego|  
|...|  
  
## <a name="navigation"></a>Nawigacja  
 Operator nawigacji relacji umożliwia przechodzenie przez relację z jednej encji (od końca) do drugiej (do końca). [NAVIGATE](navigate-entity-sql.md) przyjmuje typ relacji \<zakwalifikowany jako obszar nazw>. \<nazwa typu relacji>. Navigate zwraca\<ref T>, jeśli kardynalność do końca jest 1. Jeśli kardynalność do końca jest n, Kolekcja\<<Ref T>> zostaną zwrócone.  
  
 Przykład:  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Dane wyjściowe:  
  
|Addressid|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>WYBIERZ WARTOŚĆ I WYBIERZ  
  
### <a name="select-value"></a>WYBIERZ WARTOŚĆ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera select value klauzuli pominąć niejawną konstrukcję wiersza. W klauzuli WYBIERZ WARTOŚĆ można określić tylko jeden element. Gdy taka klauzula jest używana, wokół elementów w klauzuli SELECT nie jest skonstruowane żadne otoki `SELECT VALUE a`wierszy, a można utworzyć kolekcję żądanego kształtu, na przykład: .  
  
 Przykład:  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 Dane wyjściowe:  
  
|Nazwa|  
|----------|  
|Regulowany wyścig|  
|Uniwersalny stojak rowerowy|  
|Czapka z logo AWC|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]udostępnia również konstruktora wierszy do konstruowania dowolnych wierszy. Select przyjmuje jeden lub więcej elementów w projekcji i powoduje `SELECT a, b, c`rekord danych z polami, na przykład: .  
  
 Przykład:  
  
 WYBIERZ p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|Nazwa|ProductID|  
|----------|---------------|  
|Regulowany wyścig|1|  
|Uniwersalny stojak rowerowy|879|  
|Czapka z logo AWC|712|  
|...|...|  
  
## <a name="case-expression"></a>WYRAŻENIE SPRAWY  
 Wyrażenie [case](case-entity-sql.md) ocenia zestaw wyrażeń logicznych w celu określenia wyniku.  
  
 Przykład:  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Dane wyjściowe:  
  
|Wartość|  
|-----------|  
|Prawda|  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)

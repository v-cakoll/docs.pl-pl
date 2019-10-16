---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: f1dd5ba92c7b1eaf7117c9732a78e04e5d5a317a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319453"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Zwraca kolekcję obiektów z wyrażenia zapytania, które jest określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję obiektów.  
  
 `test_type`  
 Typ do testowania każdego obiektu zwróconego przez `expression` względem. Typ musi być kwalifikowany za pomocą przestrzeni nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja obiektów typu `test_type` lub typ podstawowy lub typ pochodny `test_type`. Jeśli jest określony tylko, zostaną zwrócone tylko wystąpienia `test_type` lub pustej kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie `OFTYPE` określa wyrażenie typu, które jest wydawane, aby wykonać test typu dla każdego elementu kolekcji.  Wyrażenie `OFTYPE` generuje nową kolekcję określonego typu zawierającego tylko te elementy, które były równoważne temu typowi lub podtyp.  
  
 Wyrażenie `OFTYPE` jest skrótem następującego wyrażenia zapytania:  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Mając na względzie, że Menedżer jest podtypem pracownika, następujące wyrażenie tworzy kolekcję tylko menedżerów z kolekcji Employees:  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 Istnieje również możliwość rzutowania kolekcji przy użyciu filtru typu:  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 Ze względu na to, że wszyscy kierownicy są menedżerami, powstająca kolekcja nadal zawiera wszystkie pierwotnych kierownictwa, chociaż kolekcja została teraz wpisana jako kolekcja menedżerów.  
  
 W poniższej tabeli przedstawiono zachowanie operatora `OFTYPE` na niektórych wzorcach. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|OFTYPE (kolekcja (EntityType), EntityType)|Kolekcja (EntityType)|  
|OFTYPE (kolekcja (ComplexType), ComplexType)|Generuje|  
|OFTYPE (Collection (RowType), RowType)|Generuje|  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używa operatora OFTYPE do zwracania kolekcji obiektów OnsiteCourse z kolekcji obiektów kursów. Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)

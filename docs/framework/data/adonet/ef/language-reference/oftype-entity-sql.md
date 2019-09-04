---
title: OFTYPE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: 36701a5e75e804ea541d242aaff243de0b24cec3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249795"
---
# <a name="oftype-entity-sql"></a>OFTYPE (Entity SQL)
Zwraca kolekcję obiektów z wyrażenia zapytania, które jest określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca kolekcję obiektów.  
  
 `test_type`  
 Typ do testowania każdego obiektu zwróconego przez `expression` . Typ musi być kwalifikowany za pomocą przestrzeni nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja obiektów typu `test_type`, lub typ podstawowy lub `test_type`typ pochodny. Jeśli jest określony tylko, zostaną zwrócone tylko wystąpienia `test_type` lub pustą kolekcję.  
  
## <a name="remarks"></a>Uwagi  
 `OFTYPE` Wyrażenie określa wyrażenie typu, które zostało wystawione w celu przeprowadzenia testu typu dla każdego elementu kolekcji.  `OFTYPE` Wyrażenie tworzy nową kolekcję określonego typu zawierającego tylko te elementy, które były równoważne temu typowi lub podtyp.  
  
 `OFTYPE` Wyrażenie jest skrótem następującego wyrażenia zapytania:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Mając na względzie, że Menedżer jest podtypem pracownika, następujące wyrażenie tworzy kolekcję tylko menedżerów z kolekcji Employees:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 Istnieje również możliwość rzutowania kolekcji przy użyciu filtru typu:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Ze względu na to, że wszyscy kierownicy są menedżerami, powstająca kolekcja nadal zawiera wszystkie pierwotnych kierownictwa, chociaż kolekcja została teraz wpisana jako kolekcja menedżerów.  
  
 W poniższej tabeli przedstawiono zachowanie `OFTYPE` operatora względem niektórych wzorców. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|OFTYPE (kolekcja (EntityType), EntityType)|Kolekcja (EntityType)|  
|OFTYPE (kolekcja (ComplexType), ComplexType)|Generuje|  
|OFTYPE (Collection (RowType), RowType)|Generuje|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora OFTYPE do zwrócenia kolekcji obiektów OnsiteCourse z kolekcji obiektów kursów. Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)

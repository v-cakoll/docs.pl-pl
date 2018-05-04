---
title: OFTYPE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: e33d613f290338d63a232bf78e7ebd0826c19897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="oftype-entity-sql"></a>OFTYPE (jednostka SQL)
Zwraca kolekcję obiektów z wyrażenia zapytania, który jest określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję obiektów.  
  
 `test_type`  
 Do przetestowania każdego obiektu zwróconego przez typ `expression` przed. Typ musi być kwalifikowana przez przestrzeni nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja obiektów typu `test_type`, lub typu podstawowego lub typu pochodnego `test_type`. Jeśli jest określony tylko tylko wystąpienia o `test_type` lub pustej kolekcji zostaną zwrócone.  
  
## <a name="remarks"></a>Uwagi  
 `OFTYPE` Wyrażenie określa wyrażenie typu, które wydaje się przeprowadzić test typu względem każdego elementu w kolekcji.  `OFTYPE` Wyrażenie zwraca nową kolekcję określonego typu zawierającego tylko elementy, które zostały odpowiednikiem tego typu lub podtyp go.  
  
 `OFTYPE` Wyrażenie stanowi skrót od następujących wyrażenia zapytania:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Biorąc pod uwagę, że Menedżer jest podtypem pracownika, poniższe wyrażenie tworzy kolekcję tylko menedżerów z kolekcji pracowników:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 Istnieje również możliwość maksymalnie rzutowania kolekcji przy użyciu filtru typu:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Ponieważ wszystkich przedstawicieli kadry kierowniczej menedżerów, wynikowy kolekcji nadal zawiera wszystkie kierownicy oryginalnej, chociaż kolekcji jest teraz typu kolekcji menedżerów.  
  
 W poniższej tabeli przedstawiono zachowania `OFTYPE` operator przez niektóre wzorce. Wszystkie wyjątki zostaną zgłoszone po stronie klienta, zanim dostawca jest wywoływany:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Elementem Collection(EntityType)|  
|OFTYPE(Collection(complexType), ComplexType)|Zgłasza wyjątek|  
|OFTYPE(Collection(RowType), RowType)|Zgłasza wyjątek|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora OFTYPE zwracać kolekcję OnsiteCourse obiektów z kolekcji oczywiście obiekty. Zapytanie jest oparta na [modelu służbowe](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

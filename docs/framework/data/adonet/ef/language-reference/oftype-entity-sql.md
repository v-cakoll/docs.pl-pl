---
title: OFTYPE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: bbc3ffd4902fe8c1c41aebe88317d0e3c32f7771
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077098"
---
# <a name="oftype-entity-sql"></a>OFTYPE (jednostka SQL)
Zwraca kolekcję obiektów z wyrażenie zapytania, które jest określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję obiektów.  
  
 `test_type`  
 Typ do przetestowania każdego obiektu zwróconego przez `expression` względem. Typ musi być kwalifikowana przez obszar nazw.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja obiektów typu `test_type`, lub typu podstawowego lub typ pochodny `test_type`. Jeśli jest określony, tylko tylko wystąpienia z `test_type` lub pusta Kolekcja zostanie zwrócony.  
  
## <a name="remarks"></a>Uwagi  
 `OFTYPE` Wyrażenie określa wyrażenie typu, który jest wystawiony dla wykonywania testu typu dla każdego elementu kolekcji.  `OFTYPE` Wyrażenie tworzy nową kolekcję określonego typu, zawierający tylko te elementy, które zostały odpowiednikiem tego typu lub podtyp go.  
  
 `OFTYPE` Wyrażenie jest skrótem następującego wyrażenia kwerendy:  
  
```  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 Biorąc pod uwagę, że Menedżer jest podtypem pracowników, poniższe wyrażenie daje kolekcję tylko menedżerowie z kolekcji pracowników:  
  
```  
OfType(employees, NamespaceName.Manager)  
```  
  
 Istnieje również możliwość nawet rzutowania kolekcji za pomocą filtru typu:  
  
```  
OfType(executives, NamespaceName.Manager)  
```  
  
 Ponieważ wszyscy przedstawiciele kadry kierowniczej menedżerów, wynikowy kolekcji nadal zawiera wszystkie oryginalne przedstawiciele kadry kierowniczej, chociaż kolekcji jest teraz wpisane jako kolekcja menedżerów.  
  
 W poniższej tabeli przedstawiono zachowania `OFTYPE` operatora przez niektóre wzorce. Wszystkie wyjątki są zgłaszane po stronie klienta, przed wywołaniem dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|OFTYPE(Collection(EntityType), EntityType)|Collection(EntityType)|  
|OFTYPE(Collection(complexType), ComplexType)|Zgłasza wyjątek|  
|OFTYPE(Collection(RowType), RowType)|Zgłasza wyjątek|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora OFTYPE zwracać kolekcję OnsiteCourse obiektów z kolekcji oczywiście obiekty. Zapytanie jest oparty na [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#OFTYPE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#oftype)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

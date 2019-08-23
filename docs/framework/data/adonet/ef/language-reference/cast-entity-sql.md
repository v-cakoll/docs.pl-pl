---
title: RZUTowanie (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 253dcf092deadd1049d0556af4ea0630602110d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935818"
---
# <a name="cast-entity-sql"></a>RZUTowanie (Entity SQL)
Konwertuje wyrażenie jednego typu danych na inne.  
  
## <a name="syntax"></a>Składnia  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie, które jest konwertowane `data_type`na.  
  
 `data_type`  
 Docelowy typ danych dostarczany przez system. Musi to być typ pierwotny (skalarny). `data_type` Użycie zależy od przestrzeni zapytania. Jeśli zapytanie jest wykonywane z <xref:System.Data.EntityClient.EntityCommand>, typ danych jest typem zdefiniowanym w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [Specyfikacja CSDL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Jeśli zapytanie jest wykonywane z <xref:System.Data.Objects.ObjectQuery%601>, typem danych jest typ środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca tę samą wartość, `data_type`co.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie cast ma podobną semantykę wyrażenia konwersji Transact-SQL. Wyrażenie cast służy do konwertowania wartości jednego typu na wartość innego typu.  
  
```  
CAST( e as T )  
```  
  
 Jeśli e jest typu S, a S jest konwertowany na T, powyższe wyrażenie jest prawidłowym wyrażeniem rzutowania. T musi być typem pierwotnym (skalarnym).  
  
 Wartości dla aspektów dokładności i skalowania mogą opcjonalnie być podane podczas rzutowania `Edm.Decimal`do. Jeśli nie podano ich jawnie, domyślne wartości dokładności i skali są odpowiednio 18 i 0. W szczególnych przypadkach obsługiwane `Decimal`są następujące przeciążenia:  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Użycie wyrażenia Cast jest uznawane za jawną konwersję. Konwersje jawne mogą obciąć dane lub utracić precyzję.  
  
> [!NOTE]
> RZUTowanie jest obsługiwane tylko dla typów pierwotnych i typów elementów członkowskich wyliczenia.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora Cast do rzutowania wyrażenia jednego typu danych na inny. Zapytanie jest oparte na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1. Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.  
  
2. Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

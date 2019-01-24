---
title: RZUTOWANIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 4d04347025de53add09f50646f1e2934b7959048
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568546"
---
# <a name="cast-entity-sql"></a>RZUTOWANIE (jednostka SQL)
Konwertuje wyrażenie jednego typu danych do innego.  
  
## <a name="syntax"></a>Składnia  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie, który jest konwertowany na `data_type`.  
  
 `data_type`  
 Typ danych dostarczane przez system docelowy. Musi być typem pierwotnym (skalarne). `data_type` Używany jest zależna od miejsca zapytania. Jeśli zapytanie jest wykonywane przy użyciu <xref:System.Data.EntityClient.EntityCommand>, typ danych jest typem zdefiniowanym w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [Specyfikacja CSDL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Jeśli zapytanie jest wykonywane przy użyciu <xref:System.Data.Objects.ObjectQuery%601>, typ danych jest typ środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca taką samą wartość jak `data_type`.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie cast przypomina semantykę [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] konwersji wyrażenia. Wyrażenie cast jest używana do konwersji wartości z jednego typu na wartość z zakresu innego typu.  
  
```  
CAST( e as T )  
```  
  
 Jeśli e jest niektórych typów S i S jest konwertowany na T, a następnie powyżej wyrażenie jest wyrażeniem rzutowania prawidłowe. T musi być typem pierwotnym (skalarne).  
  
 Opcjonalnie można podać aspektami dokładności i skali, gdy Rzutowanie na wartości `Edm.Decimal`. Jeśli nie zostały jawnie, wartości domyślne dla dokładności i skali są 18 i 0. W szczególności następujące przeciążenia są obsługiwane w przypadku `Decimal`:  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Użyj wyrażenia rzutującego jest uważany za jawnej konwersji. Konwersje jawne mogą obcięcia danych lub utratę precyzji.  
  
> [!NOTE]
>  RZUTOWANIE jest obsługiwane tylko typy pierwotne oraz typy elementów członkowskich wyliczenia.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora RZUTOWANIA w celu rzutowania wyrażenia jednego typu danych do innego. Zapytanie jest oparty na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż poniższe zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Zobacz także
- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

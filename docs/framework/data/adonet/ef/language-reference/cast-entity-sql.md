---
title: RZUTOWANIE (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: b3ebd4a7fe9d9e1324210d9f4d1265115bd8617f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cast-entity-sql"></a>RZUTOWANIE (jednostka SQL)
Konwertuje wyrażenie jednego typu danych na inny.  
  
## <a name="syntax"></a>Składnia  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Prawidłowe wyrażenie, które można przekonwertować na typ `data_type`.  
  
 `data_type`  
 Typ danych dostarczane przez system docelowy. Musi być typem pierwotnym (skalarne). `data_type` Używany jest zależna od miejsca zapytania. Jeśli zapytanie jest wykonywane z <xref:System.Data.EntityClient.EntityCommand>, typ danych jest typ zdefiniowany w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [specyfikacji pliku CSDL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md). Jeśli zapytanie jest wykonywane z <xref:System.Data.Objects.ObjectQuery%601>, typ danych jest typu wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR).  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca taką samą wartość jak `data_type`.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie cast przypomina semantykę [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] konwersji wyrażenia. Wyrażenie cast jest używana do konwertowania wartości typu jeden do wartości innego typu.  
  
```  
CAST( e as T )  
```  
  
 Jeśli e jest typu S i S jest możliwe do przekonwertowania na T, a następnie powyżej wyrażenie jest wyrażeniem rzutowania prawidłowe. T musi być typem pierwotnym (skalarne).  
  
 Opcjonalnie można podać aspektami precyzję i skalę, kiedy następuje rzutowanie do wartości `Edm.Decimal`. Jeśli nie zostało określone, wartości domyślne dla precision i scale odpowiednio są 18 i 0. W szczególności następujące przeciążenia są obsługiwane w przypadku `Decimal`:  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 Jawna konwersja jest rozważyć użycie wyrażeniem rzutowania. Jawne konwersje może obciąć danych lub utratę dokładności.  
  
> [!NOTE]
>  RZUTOWANIE jest obsługiwane tylko typy pierwotne i typy wyliczeniowe elementu członkowskiego.  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora RZUTOWANIA w celu rzutowania wyrażenia jednego typu danych na inny. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

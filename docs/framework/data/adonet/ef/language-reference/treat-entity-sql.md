---
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 06c4200434f443446e8981dcefe2baf43b1af4b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149898"
---
# <a name="treat-entity-sql"></a>TREAT (Entity SQL)
Traktuje obiekt określonego typu podstawowego jako obiekt określonego typu pochodnego.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne prawidłowe wyrażenie kwerendy zwracane encję.  
  
> [!NOTE]
> Typ określonego wyrażenia musi być podtypem określonego typu danych lub typ danych musi być podtypem typu wyrażenia.  
  
 `type`  
 Typ jednostki. Typ musi być kwalifikowany przez obszar nazw.  
  
> [!NOTE]
> Określone wyrażenie musi być podtypem określonego typu danych lub typ danych musi być podtypem wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość określonego typu danych.  
  
## <a name="remarks"></a>Uwagi  
 TREAT jest używany do wykonywania upcasting między powiązanych klas. Na przykład, `Employee` jeśli `Person` pochodzi z i `Person` `TREAT(p AS NamespaceName.Employee)` p jest typu `Person` , `Employee`upcasts ogólne wystąpienie do ; oznacza to, że pozwala na `Employee`traktowanie p jako .  
  
 TREAT jest używany w scenariuszach dziedziczenia, w których można wykonać kwerendę, podobną do następującej:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 Ta kwerenda `Person` upcasts `Employee` jednostek do typu. Jeśli wartość p nie jest `Employee`faktycznie typu, wyrażenie `null`daje wartość .  
  
> [!NOTE]
> Określone wyrażenie `Employee` musi być podtypem określonego `Person`typu danych lub typ danych musi być podtypem wyrażenia. W przeciwnym razie wyrażenie spowoduje błąd w czasie kompilacji.  
  
 W poniższej tabeli przedstawiono zachowanie leczenia przez niektóre typowe wzorce i niektóre mniej typowe wzorce. Wszystkie wyjątki są generowane od strony klienta, zanim dostawca zostanie wywołany:  
  
|Wzorce|Zachowanie|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Zwraca wartość `DbNull`.|  
|`TREAT (null AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (null AS RowType)`|Zgłasza wyjątek/|  
|`TREAT (EntityType AS EntityType)`|Zwraca `EntityType` `null`lub .|  
|`TREAT (ComplexType AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (RowType AS RowType)`|Zgłasza wyjątek.|  
  
## <a name="example"></a>Przykład  
 Poniższa [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kwerenda używa TREAT operator do konwersji obiektu typu Course do kolekcji obiektów typu OnsiteCourse. Kwerenda jest oparta na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)

---
title: Traktuj (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 38099fa83ed78b40d46faeb5e617157f7aa7c1a1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319262"
---
# <a name="treat-entity-sql"></a>Traktuj (Entity SQL)
Traktuje obiekt określonego typu podstawowego jako obiekt określonego typu pochodnego.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Każde prawidłowe wyrażenie zapytania, które zwraca jednostkę.  
  
> [!NOTE]
> Typ określonego wyrażenia musi być podtypem określonego typu danych lub typ danych musi być podtypem typu wyrażenia.  
  
 `type`  
 Typ jednostki. Typ musi być kwalifikowany za pomocą przestrzeni nazw.  
  
> [!NOTE]
> Określone wyrażenie musi być podtypem określonego typu danych lub typem danych musi być podtyp wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość określonego typu danych.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja Traktuj służy do przeprowadzenia rzutowania między powiązanymi klasami. Na przykład jeśli `Employee` pochodzi z `Person`, a p jest typu `Person`, `TREAT(p AS NamespaceName.Employee)` przyrzutuje wystąpienie generycznego `Person` `Employee`; oznacza to, że umożliwia traktowanie p jako `Employee`.  
  
 TRAKTOWANIe jest używane w scenariuszach dziedziczenia, w których można wykonywać zapytania podobne do następujących:  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 To zapytanie przerzutuje jednostki `Person` na typ `Employee`. Jeśli wartość p nie jest faktycznie typu `Employee`, wyrażenie daje wartość `null`.  
  
> [!NOTE]
> Określone wyrażenie `Employee` musi być podtypem określonego typu danych `Person` lub typem danych musi być podtyp wyrażenia. W przeciwnym razie wyrażenie spowoduje błąd czasu kompilacji.  
  
 W poniższej tabeli przedstawiono zachowanie traktowania niektórych typowych wzorców i mniej popularnych wzorców. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Zwraca `DbNull`.|  
|`TREAT (null AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (null AS RowType)`|Zgłasza wyjątek/|  
|`TREAT (EntityType AS EntityType)`|Zwraca `EntityType` lub `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (RowType AS RowType)`|Zgłasza wyjątek.|  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używa operatora Traktuj do konwersji obiektu typu kursu do kolekcji obiektów typu OnsiteCourse. Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)

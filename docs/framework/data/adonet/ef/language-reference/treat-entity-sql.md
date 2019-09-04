---
title: Traktuj (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: b7393bef32b3e057eca51eb516cb72cd2de126c2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248969"
---
# <a name="treat-entity-sql"></a>Traktuj (Entity SQL)
Traktuje obiekt określonego typu podstawowego jako obiekt określonego typu pochodnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 Funkcja Traktuj służy do przeprowadzenia rzutowania między powiązanymi klasami. Na przykład, jeśli `Employee` pochodzi od `Person` i p jest typu `Person`, `TREAT(p AS NamespaceName.Employee)` rzutuje wystąpienie ogólne `Person` na `Employee`; oznacza to, że umożliwia traktowanie p jako `Employee`.  
  
 TRAKTOWANIe jest używane w scenariuszach dziedziczenia, w których można wykonywać zapytania podobne do następujących:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 To zapytanie przerzutuje `Person` jednostki `Employee` na typ. Jeśli wartość p nie jest faktycznie typu `Employee`, wyrażenie zwraca wartość. `null`  
  
> [!NOTE]
> Określone wyrażenie `Employee` musi być podtypem określonego typu `Person`danych lub typem danych musi być podtyp wyrażenia. W przeciwnym razie wyrażenie spowoduje błąd czasu kompilacji.  
  
 W poniższej tabeli przedstawiono zachowanie traktowania niektórych typowych wzorców i mniej popularnych wzorców. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Zwraca `DbNull`wartość.|  
|`TREAT (null AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (null AS RowType)`|Zgłasza wyjątek/|  
|`TREAT (EntityType AS EntityType)`|Zwraca `EntityType` lub `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (RowType AS RowType)`|Zgłasza wyjątek.|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora Traktuj do konwersji obiektu typu kursu do kolekcji obiektów typu OnsiteCourse. Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Typy strukturalne dopuszczające wartości Null](nullable-structured-types-entity-sql.md)

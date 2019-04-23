---
title: TRAKTUJ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: e1382c4daa513477011a1d1c2132840dfae84de0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077345"
---
# <a name="treat-entity-sql"></a>TRAKTUJ (jednostka SQL)
Traktuje obiektu określonego typu podstawowego, jako obiekt określonego typu pochodnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Dowolne wyrażenie prawidłową kwerendę, która zwraca jednostkę.  
  
> [!NOTE]
>  Typ określonego wyrażenie musi być podtypem elementów określonego typu danych lub typ danych musi być podtypem typu wyrażenia.  
  
 `type`  
 Typ jednostki. Typ musi być kwalifikowana przez obszar nazw.  
  
> [!NOTE]
>  Określone wyrażenie musi być podtypem elementów określonego typu danych lub typ danych musi być podtypem wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość na określony typ danych.  
  
## <a name="remarks"></a>Uwagi  
 TRAKTUJ jest używany do wykonywania Rzutowanie rozszerzające między powiązanymi klasami. Na przykład jeśli `Employee` pochodzi od klasy `Person` i p jest typu `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a ogólny `Person` wystąpienia do `Employee`; oznacza to, że umożliwia traktowanie p jako `Employee`.  
  
 TRAKTUJ jest używany w scenariuszach dziedziczenia, w których można wykonują zapytania podobne do następujących:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 To zapytanie upcasts `Person` jednostki `Employee` typu. Jeśli wartość p nie jest faktycznie typu `Employee`, wyrażenie daje wartość `null`.  
  
> [!NOTE]
>  Określone wyrażenie `Employee` musi być podtypem typu danych określonego `Person`, lub typ danych musi być podtypem wyrażenia. W przeciwnym wypadku wyrażenie spowoduje błąd kompilacji.  
  
 W poniższej tabeli przedstawiono zachowania Traktuj przez niektóre typowe wzorce i pewne mniej typowe wzorce. Wszystkie wyjątki są zgłaszane po stronie klienta, przed wywołaniem pobiera dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Zwraca `DbNull`.|  
|`TREAT (null AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (null AS RowType)`|Zgłasza wyjątek /|  
|`TREAT (EntityType AS EntityType)`|Zwraca `EntityType` lub `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (RowType AS RowType)`|Zgłasza wyjątek.|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora TRAKTUJ można przekonwertować obiektu typu kursu do kolekcji obiektów typu OnsiteCourse. Zapytanie jest oparty na [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Typy strukturalne dopuszczające wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)

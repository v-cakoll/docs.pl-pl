---
title: TRAKTUJ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 932f335bf6a502b031dcf09b8050e278a0bbe9f8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763979"
---
# <a name="treat-entity-sql"></a>TRAKTUJ (jednostka SQL)
Traktuje obiektu określonego typu podstawowego jako obiekt określonego typu pochodnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a>Argumenty  
 `expression`  
 Wszystkie prawidłowe zapytanie zwracające jednostki.  
  
> [!NOTE]
>  Typ określonego wyrażenia musi być podtypem określonego typu danych lub typ danych musi być podtypem typu wyrażenia.  
  
 `type`  
 Typ jednostki. Typ musi być kwalifikowana przez przestrzeni nazw.  
  
> [!NOTE]
>  Określone wyrażenie musi być podtypem określonego typu danych lub typ danych musi być podtypem wyrażenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość określonego typu danych.  
  
## <a name="remarks"></a>Uwagi  
 TRAKTUJ służy do wykonywania rzutowanie w górę między powiązanymi klasami. Na przykład jeśli `Employee` pochodną `Person` i p jest typu `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a ogólny `Person` wystąpienie do `Employee`; oznacza to, umożliwia można traktować p `Employee`.  
  
 TRAKTUJ jest używany w scenariuszach dziedziczenia, w którym można wykonać zapytania podobne do poniższych:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 To zapytanie upcasts `Person` jednostki do `Employee` typu. Jeśli wartość p nie jest rzeczywiście typu `Employee`, wyrażenie daje w wyniku wartość `null`.  
  
> [!NOTE]
>  Określone wyrażenie `Employee` musi być podtypem typu danych określonego `Person`, lub typ danych musi być podtypem wyrażenia. W przeciwnym razie wartość wyrażenia spowoduje błąd kompilacji.  
  
 W poniższej tabeli przedstawiono zachowania Traktuj przez niektóre typowe wzorce i pewne mniej typowe wzorce. Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem pobiera dostawcy:  
  
|Wzorzec|Zachowanie|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|Zwraca `DbNull`.|  
|`TREAT (null AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (null AS RowType)`|Zgłasza wyjątek /|  
|`TREAT (EntityType AS EntityType)`|Zwraca `EntityType` lub `null`.|  
|`TREAT (ComplexType AS ComplexType)`|Zgłasza wyjątek.|  
|`TREAT (RowType AS RowType)`|Zgłasza wyjątek.|  
  
## <a name="example"></a>Przykład  
 Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora TRAKTUJ można przekonwertować obiektu typu kursu do kolekcji obiektów typu OnsiteCourse. Zapytanie jest oparta na [modelu służbowe](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Typy strukturalne dopuszczające wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)

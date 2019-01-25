---
title: Typy strukturalne dopuszczające wartości zerowe (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: c4b0584283e179be2661e518d5bb350b536b058f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731767"
---
# <a name="nullable-structured-types-entity-sql"></a>Typy strukturalne dopuszczające wartości zerowe (jednostka SQL)
A `null` wystąpienia typu ze strukturą to wystąpienie, który nie istnieje. To różni się od istniejącego wystąpienia, w którym ma wszystkie właściwości `null` wartości.  
  
 W tym temacie opisano dopuszczający ze strukturą, w tym typy dopuszczają wartości null i wzorce, które kodu produktu `null` wystąpień typy strukturalne dopuszczające wartość null.  
  
## <a name="kinds-of-nullable-structured-types"></a>Rodzaje typy strukturalne dopuszczające wartości zerowe  
 Istnieją trzy rodzaje typów nullable struktury:  
  
-   Typy wierszy.  
  
-   Typy złożone.  
  
-   Typy jednostek.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Wzorce kodu, które tworzą Null wystąpień typów strukturalnych  
 Następujące scenariusze tworzenia `null` wystąpień:  
  
-   Kształtowanie `null` jako typ ze strukturą:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   Rzutowanie rozszerzające typu podstawowego na pochodny typ:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   Sprzężenie zewnętrzne, pod warunkiem false:  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --or  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --or  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   Wyłuskanie `null` odwołania:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   Uzyskiwanie ANYELEMENT z pustą kolekcję:  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   Sprawdzanie `null` wystąpień typów strukturalnych:  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

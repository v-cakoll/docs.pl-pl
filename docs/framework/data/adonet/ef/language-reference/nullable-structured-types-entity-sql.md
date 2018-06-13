---
title: Typy dopuszczające wartości zerowe strukturalne (jednostki SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6b949cebfa1b16f8e6fb5a133c61c5668d90b3bf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762390"
---
# <a name="nullable-structured-types-entity-sql"></a>Typy dopuszczające wartości zerowe strukturalne (jednostki SQL)
A `null` wystąpienia typu strukturalnego to wystąpienie nie istnieje. To różni się od istniejącego wystąpienia, w którym ma wszystkie właściwości `null` wartości.  
  
 W tym temacie opisano typy dopuszczające wartości zerowe strukturalnych, w tym typy, które dopuszczają wartości null i które kodu wzorce produktu `null` wystąpień strukturalnych typy dopuszczające wartości zerowe.  
  
## <a name="kinds-of-nullable-structured-types"></a>Typy strukturalne typy dopuszczające wartości zerowe  
 Istnieją trzy rodzaje typy dopuszczające wartości zerowe struktury:  
  
-   Typy wierszy.  
  
-   Typy złożone.  
  
-   Typy jednostek.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Wzorce kodu, które powodują powstanie Null wystąpień typów strukturalnych  
 Następujące scenariusze tworzenia `null` wystąpień:  
  
-   Kształtowania `null` jako typ strukturalny:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   Rzutowanie w górę do typem pochodnym typu podstawowego:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   Sprzężenie zewnętrzne na fałszywego warunku:  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --lub  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --lub  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   Dereferencji `null` odwołania:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   Uzyskiwanie ANYELEMENT z pustej kolekcji:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)

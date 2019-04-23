---
title: Typy strukturalne dopuszczające wartości zerowe (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 632b092e1d0d99a2a40cc3cd4b323e234de6232b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127858"
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

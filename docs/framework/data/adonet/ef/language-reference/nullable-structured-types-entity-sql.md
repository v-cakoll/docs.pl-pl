---
title: "Typy dopuszczające wartości zerowe strukturalne (jednostki SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3f294088e92951e964c3daa2a105b767bca1d288
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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

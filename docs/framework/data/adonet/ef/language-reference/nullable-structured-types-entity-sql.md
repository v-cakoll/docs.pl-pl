---
title: Typy strukturalne dopuszczające wartość null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: 6b078ae458aba73e82957f84408b1000b216aef9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249814"
---
# <a name="nullable-structured-types-entity-sql"></a>Typy strukturalne dopuszczające wartość null (Entity SQL)
`null` Wystąpienie typu strukturalnego jest wystąpieniem, które nie istnieje. Różni się to od istniejącego wystąpienia, w którym wszystkie właściwości mają `null` wartości.  
  
 W tym temacie opisano typy strukturalne dopuszczające wartość null, w tym typy dopuszczające wartości `null` null i które wzorce kodu tworzą wystąpienia typów ze strukturą dopuszczającą wartość null.  
  
## <a name="kinds-of-nullable-structured-types"></a>Rodzaje typów strukturalnych dopuszczających wartość null  
 Istnieją trzy rodzaje typów struktur dopuszczających wartości null:  
  
- Typy wierszy.  
  
- Typy złożone.  
  
- Typy jednostek.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Wzorce kodu generujące puste wystąpienia typów strukturalnych  
 Następujące scenariusze tworzą `null` wystąpienia:  
  
- Kształtowanie `null` jako typ strukturalny:  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Przerzutowanie typu podstawowego na typ pochodny:  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Sprzężenie zewnętrzne w przypadku wartości false:  
  
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
  
- Odwołuje się `null` do odwołania:  
  
    ```  
    DEREF(NullRef)  
    ```  
  
- Uzyskiwanie ANYELEMENT z pustej kolekcji:  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- `null` Sprawdzanie wystąpień typów strukturalnych:  
  
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

- [Omówienie jednostki SQL](entity-sql-overview.md)

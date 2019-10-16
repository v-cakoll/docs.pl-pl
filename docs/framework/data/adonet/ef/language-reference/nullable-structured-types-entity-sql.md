---
title: Typy strukturalne dopuszczające wartość null (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
ms.openlocfilehash: b155c672d8c0bef8b01fb26fb49908f094add25a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319487"
---
# <a name="nullable-structured-types-entity-sql"></a>Typy strukturalne dopuszczające wartość null (Entity SQL)
Wystąpienie `null` typu strukturalnego jest wystąpieniem, które nie istnieje. Różni się to od istniejącego wystąpienia, w którym wszystkie właściwości mają wartości `null`.  
  
 W tym temacie opisano typy strukturalne dopuszczające wartość null, w tym typy dopuszczające wartości null i które wzorce kodu tworzą wystąpienia `null` typów ze strukturą dopuszczającą wartość null.  
  
## <a name="kinds-of-nullable-structured-types"></a>Rodzaje typów strukturalnych dopuszczających wartość null  
 Istnieją trzy rodzaje typów struktur dopuszczających wartości null:  
  
- Typy wierszy.  
  
- Typy złożone.  
  
- Typy jednostek.  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a>Wzorce kodu generujące puste wystąpienia typów strukturalnych  
 Następujące scenariusze tworzą wystąpienia `null`:  
  
- Kształtowanie `null` jako typ strukturalny:  
  
    ```sql  
    TREAT (NULL AS StructuredType)  
    ```  
  
- Przerzutowanie typu podstawowego na typ pochodny:  
  
    ```sql  
    TREAT (BaseType AS DerivedType)  
    ```  
  
- Sprzężenie zewnętrzne w przypadku wartości false:  
  
    ```sql  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --lub  
  
    ```sql  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     --lub  
  
    ```sql  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
- Odwołujące się do `null` odwołania:  
  
    ```sql  
    DEREF(NullRef)  
    ```  
  
- Uzyskiwanie ANYELEMENT z pustej kolekcji:  
  
    ```sql  
    ANYELEMENT(EmptyCollection)  
    ```  
  
- Sprawdzanie wystąpień `null` typów strukturalnych:  
  
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

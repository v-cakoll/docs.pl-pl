---
title: Funkcja (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: bacc773351812a5db60f493f3025c8e4b07dbaa2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833801"
---
# <a name="function-entity-sql"></a>Funkcja (Entity SQL)
Definiuje funkcję w zakresie polecenia kwerendy Entity SQL.  
  
## <a name="syntax"></a>Składnia  
  
```sql  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>Argumenty  
 `function-name`  
 Nazwa funkcji.  
  
 `parameter-name`  
 Nazwa parametru w funkcji.  
  
 `function_expression`  
 Prawidłowe wyrażenie Entity SQL, które jest funkcją. Polecenie w funkcji może działać na `parameter_name` parametry przesłane do funkcji.  
  
 `data_type`  
 Nazwa obsługiwanego typu.  
  
 Kolekcja (< type_definition`>`)  
 Wyrażenie zwracające kolekcję obsługiwanych typów, wierszy lub odwołań.  
  
 REF **(** `data_type` **)**  
 Wyrażenie zwracające odwołanie do typu jednostki.  
  
 WIERSZ **(** `row_expression` **)**  
 Wyrażenie zwracające anonimowe, strukturalnie wpisane rekordy z co najmniej jednej wartości. Aby uzyskać więcej informacji, zobacz [wiersz](row-entity-sql.md).  
  
## <a name="remarks"></a>Uwagi  
 Wiele funkcji o tej samej nazwie można zadeklarować wewnętrznie, o ile sygnatury funkcji różnią się od siebie. Aby uzyskać więcej informacji, zobacz [rozpoznawanie przeciążeń funkcji](function-overload-resolution-entity-sql.md).  
  
 Wbudowaną funkcję można wywołać w Entity SQL polecenie dopiero po zdefiniowaniu tego polecenia. Jednak Wbudowana funkcja może być wywoływana wewnątrz innej wbudowanej funkcji albo przed lub po zdefiniowaniu wywoływanej funkcji. W poniższym przykładzie funkcja A wywołuje funkcję B przed zdefiniowaniem funkcji B:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Aby uzyskać więcej informacji, zobacz [instrukcje: wywoływanie funkcji zdefiniowanej przez użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).  
  
 Funkcje mogą być również deklarowane w samym modelu. Funkcje zadeklarowane w modelu są wykonywane w taki sam sposób jak funkcje zadeklarowane jako wbudowane w poleceniu. Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie Entity SQL definiuje funkcję, `Products` która pobiera wartość całkowitą do odfiltrowania zwróconych produktów.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a>Przykład  
 Następujące polecenie Entity SQL definiuje funkcję, `StringReturnsCollection` która pobiera kolekcję ciągów do filtrowania zwróconych kontaktów.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Jednostki języka SQL](entity-sql-language.md)

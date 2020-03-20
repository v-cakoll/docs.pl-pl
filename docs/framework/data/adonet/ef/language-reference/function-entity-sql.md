---
title: FUNKCJA (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: fd7f484733e7135d2d6c8094b6527d672a988088
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150301"
---
# <a name="function-entity-sql"></a>FUNKCJA (Jednostka SQL)
Definiuje funkcję w zakresie polecenia zapytania SQL jednostki.  
  
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
 Prawidłowe wyrażenie SQL jednostki, które jest funkcją. Polecenie w funkcji może `parameter_name` działać na parametrach przekazanych do funkcji.  
  
 `data_type`  
 Nazwa obsługiwanego typu.  
  
 KOLEKCJA ( <type_definition`>` )  
 Wyrażenie, które zwraca kolekcję obsługiwanych typów, wierszy lub odwołań.  
  
 REF **(**`data_type`**)**  
 Wyrażenie, które zwraca odwołanie do typu jednostki.  
  
 WIERSZ **(**`row_expression`**)**  
 Wyrażenie, które zwraca anonimowe, strukturalnie wpisane rekordy z jednej lub więcej wartości. Aby uzyskać więcej informacji, zobacz [ROW](row-entity-sql.md).  
  
## <a name="remarks"></a>Uwagi  
 Wiele funkcji o tej samej nazwie można zadeklarować w wierszu, tak długo, jak podpisy funkcji są różne. Aby uzyskać więcej informacji, zobacz [Rozpoznawanie przeciążenia funkcji](function-overload-resolution-entity-sql.md).  
  
 Funkcję wbudowaną można wywołać w poleceniu Entity SQL tylko wtedy, gdy zostało zdefiniowane w tym poleceniu. Jednak funkcja wbudowana może być wywoływana wewnątrz innej funkcji wbudowanej przed lub po zdefiniowaniu wywoływanej funkcji. W poniższym przykładzie funkcja A wywołuje funkcję B przed zdefiniowaniem funkcji B:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Aby uzyskać więcej informacji, zobacz [Jak: Wywołanie funkcji zdefiniowanej przez użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).  
  
 Funkcje można również zadeklarować w samym modelu. Funkcje zadeklarowane w modelu są wykonywane w taki sam sposób, jak funkcje zadeklarowane w wierszu polecenia. Aby uzyskać więcej informacji, zobacz [Funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie Entity SQL definiuje `Products` funkcję, która przyjmuje wartość całkowitą do filtrowania zwróconych produktów.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a>Przykład  
 Następujące polecenie Entity SQL definiuje `StringReturnsCollection` funkcję, która pobiera kolekcję ciągów do filtrowania zwracanych kontaktów.  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Jednostki języka SQL](entity-sql-language.md)

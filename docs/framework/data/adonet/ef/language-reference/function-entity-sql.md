---
title: — Funkcja (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: efab5f1abbc5e0c22e404c37dc80dd5aafa09ce1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106369"
---
# <a name="function-entity-sql"></a>— Funkcja (jednostka SQL)
Definiuje funkcję w zakresie polecenia zapytań jednostki SQL.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 Prawidłowe wyrażenie SQL jednostki, które jest funkcją. Polecenia w funkcji może działać na `parameter_name` parametry przekazywane do funkcji.  
  
 `data_type`  
 Nazwa obsługiwanego typu.  
  
 KOLEKCJA (< type_definition`>` )  
 Wyrażenie, które zwraca kolekcję obsługiwanych typów, wiersze lub odwołania.  
  
 REF **(**`data_type`**)**  
 Wyrażenie, które zwraca odwołanie do typu jednostki.  
  
 WIERSZ **(**`row_expression`**)**  
 Wyrażenie, które zwraca anonimowe, wpisanych strukturalnie rekordy z co najmniej jedną wartość. Aby uzyskać więcej informacji, zobacz [wiersza](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Uwagi  
 Wiele funkcji o tej samej nazwie może być zadeklarowana w tekście, tak długo, jak sygnatury funkcji są różne. Aby uzyskać więcej informacji, zobacz [rozdzielczość przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Funkcja śródwierszowa może zostać wywołany w polecenia SQL jednostki, tylko wtedy, gdy zdefiniowano już tego polecenia. Jednak wbudowanej funkcji można wywołać wewnątrz innego funkcja śródwierszowa, przed lub po zdefiniowaniu wywołanej funkcji. W poniższym przykładzie funkcja A wywołuje funkcję B, zanim funkcja B jest zdefiniowana:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie funkcji zdefiniowanej przez użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).  
  
 Funkcje mogą być także zadeklarowane w samym modelu. Funkcje zadeklarowane w modelu są wykonywane w taki sam sposób jak funkcje zadeklarowane wbudowanego w poleceniu. Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie SQL jednostki definiuje funkcję `Products` , przyjmuje wartość całkowitą do filtrowania produktów zwrócone.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie SQL jednostki definiuje funkcję `StringReturnsCollection` przyjmującej Kolekcja ciągów do filtrowania zwrócone kontaktów.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do języka Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Język Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

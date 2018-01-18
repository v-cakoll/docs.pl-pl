---
title: Funkcja (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 957c31d3262e5c97d576d444748bd1979aee0ce0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="function-entity-sql"></a>Funkcja (jednostka SQL)
Definiuje funkcję w zakresie polecenia zapytania SQL jednostki.  
  
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
 Prawidłowe wyrażenie SQL jednostki, które jest funkcją. Polecenia w funkcji może działać na `parameter_name` parametrów przekazanych do funkcji.  
  
 `data_type`  
 Nazwa obsługiwanego typu.  
  
 KOLEKCJA (< type_definition`>` )  
 Wyrażenie, które zwraca kolekcję obsługiwanych typów, wierszy i odwołań.  
  
 REF **(**`data_type`**)**  
 Wyrażenie, które zwraca odwołanie do typu jednostki.  
  
 WIERSZ **(**`row_expression`**)**  
 Wyrażenie, które zwraca anonimowe, wpisana strukturę rekordów z co najmniej jedną wartość. Aby uzyskać więcej informacji, zobacz [wiersza](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Uwagi  
 Wiele funkcji o tej samej nazwie może być zadeklarowana w tekście, tak długo, jak sygnatury funkcji są różne. Aby uzyskać więcej informacji, zobacz [rozpoznawanie przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Wbudowanej funkcji może zostać wywołany w poleceniu SQL jednostki, tylko wtedy, gdy została ona zdefiniowana w tym poleceniu. Jednak wbudowanej funkcji można wywołać wewnątrz innej funkcji wbudowanej przed lub po zdefiniowaniu wywoływana funkcja. W poniższym przykładzie wywołania funkcji A działać B przed zdefiniowaniem funkcja B:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Aby uzyskać więcej informacji, zobacz [porady: wywoływanie funkcji zdefiniowanych przez użytkownika](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02).  
  
 Funkcje również mogą być deklarowane w samym modelu. Funkcje zadeklarowany w modelu są wykonywane w taki sam sposób jak funkcje wbudowane zadeklarowane w poleceniu. Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie SQL jednostki definiuje funkcję `Products` który przyjmuje wartość całkowitą filtrowanie zwróconych produktów.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie SQL jednostki definiuje funkcję `StringReturnsCollection` pobierającej kolekcji ciągów w celu filtrowania zwrócony kontaktów.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Jednostki języka SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

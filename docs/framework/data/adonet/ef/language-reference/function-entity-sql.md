---
title: Funkcja (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
ms.openlocfilehash: ae8da3985f11a2e9f52852876a21f50a412e3b27
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250940"
---
# <a name="function-entity-sql"></a>Funkcja (Entity SQL)
Definiuje funkcję w zakresie polecenia kwerendy Entity SQL.  
  
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
 Prawidłowe wyrażenie Entity SQL, które jest funkcją. Polecenie w funkcji może działać na `parameter_name` parametrach przekazaną do funkcji.  
  
 `data_type`  
 Nazwa obsługiwanego typu.  
  
 Kolekcja (< type_definition`>` )  
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
  
 Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie funkcji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))zdefiniowanej przez użytkownika.  
  
 Funkcje mogą być również deklarowane w samym modelu. Funkcje zadeklarowane w modelu są wykonywane w taki sam sposób jak funkcje zadeklarowane jako wbudowane w poleceniu. Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie Entity SQL definiuje funkcję `Products` , która pobiera liczbę całkowitą do odfiltrowania zwróconych produktów.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Przykład  
 Następujące polecenie Entity SQL definiuje funkcję `StringReturnsCollection` pobierającą ciągi do filtrowania zwróconych kontaktów.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Jednostki języka SQL](entity-sql-language.md)

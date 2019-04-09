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
# <a name="function-entity-sql"></a><span data-ttu-id="13c16-102">— Funkcja (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="13c16-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="13c16-103">Definiuje funkcję w zakresie polecenia zapytań jednostki SQL.</span><span class="sxs-lookup"><span data-stu-id="13c16-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c16-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13c16-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="13c16-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="13c16-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="13c16-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="13c16-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="13c16-107">Nazwa parametru w funkcji.</span><span class="sxs-lookup"><span data-stu-id="13c16-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="13c16-108">Prawidłowe wyrażenie SQL jednostki, które jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="13c16-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="13c16-109">Polecenia w funkcji może działać na `parameter_name` parametry przekazywane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="13c16-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="13c16-110">Nazwa obsługiwanego typu.</span><span class="sxs-lookup"><span data-stu-id="13c16-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="13c16-111">KOLEKCJA (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="13c16-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="13c16-112">Wyrażenie, które zwraca kolekcję obsługiwanych typów, wiersze lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="13c16-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="13c16-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="13c16-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="13c16-114">Wyrażenie, które zwraca odwołanie do typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="13c16-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="13c16-115">WIERSZ **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="13c16-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="13c16-116">Wyrażenie, które zwraca anonimowe, wpisanych strukturalnie rekordy z co najmniej jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="13c16-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="13c16-117">Aby uzyskać więcej informacji, zobacz [wiersza](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="13c16-117">For more information, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13c16-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13c16-118">Remarks</span></span>  
 <span data-ttu-id="13c16-119">Wiele funkcji o tej samej nazwie może być zadeklarowana w tekście, tak długo, jak sygnatury funkcji są różne.</span><span class="sxs-lookup"><span data-stu-id="13c16-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="13c16-120">Aby uzyskać więcej informacji, zobacz [rozdzielczość przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="13c16-120">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="13c16-121">Funkcja śródwierszowa może zostać wywołany w polecenia SQL jednostki, tylko wtedy, gdy zdefiniowano już tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="13c16-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="13c16-122">Jednak wbudowanej funkcji można wywołać wewnątrz innego funkcja śródwierszowa, przed lub po zdefiniowaniu wywołanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="13c16-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="13c16-123">W poniższym przykładzie funkcja A wywołuje funkcję B, zanim funkcja B jest zdefiniowana:</span><span class="sxs-lookup"><span data-stu-id="13c16-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="13c16-124">Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie funkcji zdefiniowanej przez użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="13c16-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="13c16-125">Funkcje mogą być także zadeklarowane w samym modelu.</span><span class="sxs-lookup"><span data-stu-id="13c16-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="13c16-126">Funkcje zadeklarowane w modelu są wykonywane w taki sam sposób jak funkcje zadeklarowane wbudowanego w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="13c16-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="13c16-127">Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="13c16-127">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13c16-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="13c16-128">Example</span></span>  
 <span data-ttu-id="13c16-129">Poniższe polecenie SQL jednostki definiuje funkcję `Products` , przyjmuje wartość całkowitą do filtrowania produktów zwrócone.</span><span class="sxs-lookup"><span data-stu-id="13c16-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="13c16-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="13c16-130">Example</span></span>  
 <span data-ttu-id="13c16-131">Poniższe polecenie SQL jednostki definiuje funkcję `StringReturnsCollection` przyjmującej Kolekcja ciągów do filtrowania zwrócone kontaktów.</span><span class="sxs-lookup"><span data-stu-id="13c16-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="13c16-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13c16-132">See also</span></span>

- [<span data-ttu-id="13c16-133">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="13c16-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="13c16-134">Język Entity SQL</span><span class="sxs-lookup"><span data-stu-id="13c16-134">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

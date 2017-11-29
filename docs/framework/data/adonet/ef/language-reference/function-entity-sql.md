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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 40c8f218238492bbbc4af543aa6f9a635454b359
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="function-entity-sql"></a><span data-ttu-id="13b77-102">Funkcja (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="13b77-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="13b77-103">Definiuje funkcję w zakresie polecenia zapytania SQL jednostki.</span><span class="sxs-lookup"><span data-stu-id="13b77-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13b77-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13b77-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="13b77-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="13b77-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="13b77-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="13b77-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="13b77-107">Nazwa parametru w funkcji.</span><span class="sxs-lookup"><span data-stu-id="13b77-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="13b77-108">Prawidłowe wyrażenie SQL jednostki, które jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="13b77-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="13b77-109">Polecenia w funkcji może działać na `parameter_name` parametrów przekazanych do funkcji.</span><span class="sxs-lookup"><span data-stu-id="13b77-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="13b77-110">Nazwa obsługiwanego typu.</span><span class="sxs-lookup"><span data-stu-id="13b77-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="13b77-111">KOLEKCJA (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="13b77-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="13b77-112">Wyrażenie, które zwraca kolekcję obsługiwanych typów, wierszy i odwołań.</span><span class="sxs-lookup"><span data-stu-id="13b77-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="13b77-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="13b77-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="13b77-114">Wyrażenie, które zwraca odwołanie do typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="13b77-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="13b77-115">WIERSZ **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="13b77-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="13b77-116">Wyrażenie, które zwraca anonimowe, wpisana strukturę rekordów z co najmniej jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="13b77-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="13b77-117">Aby uzyskać więcej informacji, zobacz [wiersza](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="13b77-117">For more information, see [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13b77-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13b77-118">Remarks</span></span>  
 <span data-ttu-id="13b77-119">Wiele funkcji o tej samej nazwie może być zadeklarowana w tekście, tak długo, jak sygnatury funkcji są różne.</span><span class="sxs-lookup"><span data-stu-id="13b77-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="13b77-120">Aby uzyskać więcej informacji, zobacz [rozpoznawanie przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="13b77-120">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="13b77-121">Wbudowanej funkcji może zostać wywołany w poleceniu SQL jednostki, tylko wtedy, gdy została ona zdefiniowana w tym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="13b77-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="13b77-122">Jednak wbudowanej funkcji można wywołać wewnątrz innej funkcji wbudowanej przed lub po zdefiniowaniu wywoływana funkcja.</span><span class="sxs-lookup"><span data-stu-id="13b77-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="13b77-123">W poniższym przykładzie wywołania funkcji A działać B przed zdefiniowaniem funkcja B:</span><span class="sxs-lookup"><span data-stu-id="13b77-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="13b77-124">Aby uzyskać więcej informacji, zobacz [porady: wywoływanie funkcji zdefiniowanych przez użytkownika](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02).</span><span class="sxs-lookup"><span data-stu-id="13b77-124">For more information, see [How to: Call a User-Defined Function](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02).</span></span>  
  
 <span data-ttu-id="13b77-125">Funkcje również mogą być deklarowane w samym modelu.</span><span class="sxs-lookup"><span data-stu-id="13b77-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="13b77-126">Funkcje zadeklarowany w modelu są wykonywane w taki sam sposób jak funkcje wbudowane zadeklarowane w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="13b77-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="13b77-127">Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="13b77-127">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13b77-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="13b77-128">Example</span></span>  
 <span data-ttu-id="13b77-129">Poniższe polecenie SQL jednostki definiuje funkcję `Products` który przyjmuje wartość całkowitą filtrowanie zwróconych produktów.</span><span class="sxs-lookup"><span data-stu-id="13b77-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="13b77-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="13b77-130">Example</span></span>  
 <span data-ttu-id="13b77-131">Poniższe polecenie SQL jednostki definiuje funkcję `StringReturnsCollection` pobierającej kolekcji ciągów w celu filtrowania zwrócony kontaktów.</span><span class="sxs-lookup"><span data-stu-id="13b77-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="13b77-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13b77-132">See Also</span></span>  
 [<span data-ttu-id="13b77-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="13b77-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="13b77-134">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="13b77-134">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

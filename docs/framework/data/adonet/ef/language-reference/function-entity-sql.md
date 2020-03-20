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
# <a name="function-entity-sql"></a><span data-ttu-id="7d8a9-102">FUNKCJA (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="7d8a9-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="7d8a9-103">Definiuje funkcję w zakresie polecenia zapytania SQL jednostki.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d8a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d8a9-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="7d8a9-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7d8a9-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="7d8a9-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="7d8a9-107">Nazwa parametru w funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="7d8a9-108">Prawidłowe wyrażenie SQL jednostki, które jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="7d8a9-109">Polecenie w funkcji może `parameter_name` działać na parametrach przekazanych do funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="7d8a9-110">Nazwa obsługiwanego typu.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="7d8a9-111">KOLEKCJA ( <type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="7d8a9-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="7d8a9-112">Wyrażenie, które zwraca kolekcję obsługiwanych typów, wierszy lub odwołań.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="7d8a9-113">REF **(**`data_type`**)**</span><span class="sxs-lookup"><span data-stu-id="7d8a9-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="7d8a9-114">Wyrażenie, które zwraca odwołanie do typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="7d8a9-115">WIERSZ **(**`row_expression`**)**</span><span class="sxs-lookup"><span data-stu-id="7d8a9-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="7d8a9-116">Wyrażenie, które zwraca anonimowe, strukturalnie wpisane rekordy z jednej lub więcej wartości.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="7d8a9-117">Aby uzyskać więcej informacji, zobacz [ROW](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7d8a9-117">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d8a9-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d8a9-118">Remarks</span></span>  
 <span data-ttu-id="7d8a9-119">Wiele funkcji o tej samej nazwie można zadeklarować w wierszu, tak długo, jak podpisy funkcji są różne.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="7d8a9-120">Aby uzyskać więcej informacji, zobacz [Rozpoznawanie przeciążenia funkcji](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7d8a9-120">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="7d8a9-121">Funkcję wbudowaną można wywołać w poleceniu Entity SQL tylko wtedy, gdy zostało zdefiniowane w tym poleceniu.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="7d8a9-122">Jednak funkcja wbudowana może być wywoływana wewnątrz innej funkcji wbudowanej przed lub po zdefiniowaniu wywoływanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="7d8a9-123">W poniższym przykładzie funkcja A wywołuje funkcję B przed zdefiniowaniem funkcji B:</span><span class="sxs-lookup"><span data-stu-id="7d8a9-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="7d8a9-124">Aby uzyskać więcej informacji, zobacz [Jak: Wywołanie funkcji zdefiniowanej przez użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7d8a9-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="7d8a9-125">Funkcje można również zadeklarować w samym modelu.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="7d8a9-126">Funkcje zadeklarowane w modelu są wykonywane w taki sam sposób, jak funkcje zadeklarowane w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="7d8a9-127">Aby uzyskać więcej informacji, zobacz [Funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="7d8a9-127">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d8a9-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d8a9-128">Example</span></span>  
 <span data-ttu-id="7d8a9-129">Następujące polecenie Entity SQL definiuje `Products` funkcję, która przyjmuje wartość całkowitą do filtrowania zwróconych produktów.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION1](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function1)]  
  
## <a name="example"></a><span data-ttu-id="7d8a9-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d8a9-130">Example</span></span>  
 <span data-ttu-id="7d8a9-131">Następujące polecenie Entity SQL definiuje `StringReturnsCollection` funkcję, która pobiera kolekcję ciągów do filtrowania zwracanych kontaktów.</span><span class="sxs-lookup"><span data-stu-id="7d8a9-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FUNCTION2](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="7d8a9-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d8a9-132">See also</span></span>

- [<span data-ttu-id="7d8a9-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="7d8a9-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="7d8a9-134">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="7d8a9-134">Entity SQL Language</span></span>](entity-sql-language.md)

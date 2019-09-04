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
# <a name="function-entity-sql"></a><span data-ttu-id="fb1b2-102">Funkcja (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fb1b2-102">FUNCTION (Entity SQL)</span></span>
<span data-ttu-id="fb1b2-103">Definiuje funkcję w zakresie polecenia kwerendy Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-103">Defines a function in the scope of an Entity SQL query command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb1b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb1b2-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="fb1b2-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fb1b2-105">Arguments</span></span>  
 `function-name`  
 <span data-ttu-id="fb1b2-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-106">Name of the function.</span></span>  
  
 `parameter-name`  
 <span data-ttu-id="fb1b2-107">Nazwa parametru w funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-107">Name of a parameter in the function.</span></span>  
  
 `function_expression`  
 <span data-ttu-id="fb1b2-108">Prawidłowe wyrażenie Entity SQL, które jest funkcją.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-108">A valid Entity SQL expression that is the function.</span></span> <span data-ttu-id="fb1b2-109">Polecenie w funkcji może działać na `parameter_name` parametrach przekazaną do funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-109">The command in the function can act on `parameter_name` parameters passed to the function.</span></span>  
  
 `data_type`  
 <span data-ttu-id="fb1b2-110">Nazwa obsługiwanego typu.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-110">Name of a supported type.</span></span>  
  
 <span data-ttu-id="fb1b2-111">Kolekcja (< type_definition`>` )</span><span class="sxs-lookup"><span data-stu-id="fb1b2-111">COLLECTION ( <type_definition`>` )</span></span>  
 <span data-ttu-id="fb1b2-112">Wyrażenie zwracające kolekcję obsługiwanych typów, wierszy lub odwołań.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-112">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
 <span data-ttu-id="fb1b2-113">REF **(** `data_type` **)**</span><span class="sxs-lookup"><span data-stu-id="fb1b2-113">REF **(**`data_type`**)**</span></span>  
 <span data-ttu-id="fb1b2-114">Wyrażenie zwracające odwołanie do typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-114">An expression that returns a reference to an entity type.</span></span>  
  
 <span data-ttu-id="fb1b2-115">WIERSZ **(** `row_expression` **)**</span><span class="sxs-lookup"><span data-stu-id="fb1b2-115">ROW **(**`row_expression`**)**</span></span>  
 <span data-ttu-id="fb1b2-116">Wyrażenie zwracające anonimowe, strukturalnie wpisane rekordy z co najmniej jednej wartości.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-116">An expression that returns anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="fb1b2-117">Aby uzyskać więcej informacji, zobacz [wiersz](row-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fb1b2-117">For more information, see [ROW](row-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb1b2-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb1b2-118">Remarks</span></span>  
 <span data-ttu-id="fb1b2-119">Wiele funkcji o tej samej nazwie można zadeklarować wewnętrznie, o ile sygnatury funkcji różnią się od siebie.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-119">Multiple functions with the same name can be declared inline, as long as the function signatures are different.</span></span> <span data-ttu-id="fb1b2-120">Aby uzyskać więcej informacji, zobacz [rozpoznawanie przeciążeń funkcji](function-overload-resolution-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fb1b2-120">For more information, see [Function Overload Resolution](function-overload-resolution-entity-sql.md).</span></span>  
  
 <span data-ttu-id="fb1b2-121">Wbudowaną funkcję można wywołać w Entity SQL polecenie dopiero po zdefiniowaniu tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-121">An inline function can be called in an Entity SQL command only after it has been defined in that command.</span></span> <span data-ttu-id="fb1b2-122">Jednak Wbudowana funkcja może być wywoływana wewnątrz innej wbudowanej funkcji albo przed lub po zdefiniowaniu wywoływanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-122">However, an inline function can be called inside another inline function either before or after the called function has been defined.</span></span> <span data-ttu-id="fb1b2-123">W poniższym przykładzie funkcja A wywołuje funkcję B przed zdefiniowaniem funkcji B:</span><span class="sxs-lookup"><span data-stu-id="fb1b2-123">In the following example, function A calls function B before function B is defined:</span></span>  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 <span data-ttu-id="fb1b2-124">Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie funkcji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-124">For more information, see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100)).</span></span>  
  
 <span data-ttu-id="fb1b2-125">Funkcje mogą być również deklarowane w samym modelu.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-125">Functions can also be declared in the model itself.</span></span> <span data-ttu-id="fb1b2-126">Funkcje zadeklarowane w modelu są wykonywane w taki sam sposób jak funkcje zadeklarowane jako wbudowane w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-126">Functions declared in the model are executed in the same way as functions declared inline in the command.</span></span> <span data-ttu-id="fb1b2-127">Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fb1b2-127">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb1b2-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb1b2-128">Example</span></span>  
 <span data-ttu-id="fb1b2-129">Następujące polecenie Entity SQL definiuje funkcję `Products` , która pobiera liczbę całkowitą do odfiltrowania zwróconych produktów.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-129">The following Entity SQL command defines a function `Products` that takes an integer value to filter the returned products.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a><span data-ttu-id="fb1b2-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb1b2-130">Example</span></span>  
 <span data-ttu-id="fb1b2-131">Następujące polecenie Entity SQL definiuje funkcję `StringReturnsCollection` pobierającą ciągi do filtrowania zwróconych kontaktów.</span><span class="sxs-lookup"><span data-stu-id="fb1b2-131">The following Entity SQL command defines a function `StringReturnsCollection` that takes a collection of strings to filter the returned contacts.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a><span data-ttu-id="fb1b2-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb1b2-132">See also</span></span>

- [<span data-ttu-id="fb1b2-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="fb1b2-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fb1b2-134">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="fb1b2-134">Entity SQL Language</span></span>](entity-sql-language.md)

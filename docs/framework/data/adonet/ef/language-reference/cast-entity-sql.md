---
title: RZUTOWANIE (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 353398f834aff5cefb3aed91899ce042df9df60a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cast-entity-sql"></a><span data-ttu-id="e9c9e-102">RZUTOWANIE (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="e9c9e-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="e9c9e-103">Konwertuje wyrażenie jednego typu danych na inny.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9c9e-104">Syntax</span></span>  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9c9e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e9c9e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e9c9e-106">Prawidłowe wyrażenie, które można przekonwertować na typ `data_type`.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="e9c9e-107">Typ danych dostarczane przez system docelowy.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-107">The target system-supplied data type.</span></span> <span data-ttu-id="e9c9e-108">Musi być typem pierwotnym (skalarne).</span><span class="sxs-lookup"><span data-stu-id="e9c9e-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="e9c9e-109">`data_type` Używany jest zależna od miejsca zapytania.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="e9c9e-110">Jeśli zapytanie jest wykonywane z <xref:System.Data.EntityClient.EntityCommand>, typ danych jest typ zdefiniowany w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="e9c9e-111">Aby uzyskać więcej informacji, zobacz [specyfikacji pliku CSDL](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="e9c9e-111">For more information, see [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span> <span data-ttu-id="e9c9e-112">Jeśli zapytanie jest wykonywane z <xref:System.Data.Objects.ObjectQuery%601>, typ danych jest typu wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="e9c9e-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9c9e-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e9c9e-113">Return Value</span></span>  
 <span data-ttu-id="e9c9e-114">Zwraca taką samą wartość jak `data_type`.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9c9e-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9c9e-115">Remarks</span></span>  
 <span data-ttu-id="e9c9e-116">Wyrażenie cast przypomina semantykę [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] konwersji wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-116">The cast expression has similar semantics to the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CONVERT expression.</span></span> <span data-ttu-id="e9c9e-117">Wyrażenie cast jest używana do konwertowania wartości typu jeden do wartości innego typu.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```  
CAST( e as T )  
```  
  
 <span data-ttu-id="e9c9e-118">Jeśli e jest typu S i S jest możliwe do przekonwertowania na T, a następnie powyżej wyrażenie jest wyrażeniem rzutowania prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="e9c9e-119">T musi być typem pierwotnym (skalarne).</span><span class="sxs-lookup"><span data-stu-id="e9c9e-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="e9c9e-120">Opcjonalnie można podać aspektami precyzję i skalę, kiedy następuje rzutowanie do wartości `Edm.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="e9c9e-121">Jeśli nie zostało określone, wartości domyślne dla precision i scale odpowiednio są 18 i 0.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="e9c9e-122">W szczególności następujące przeciążenia są obsługiwane w przypadku `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="e9c9e-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
-   `CAST( d as Edm.Decimal );`  
  
-   `CAST( d as Edm.Decimal(precision) );`  
  
-   `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="e9c9e-123">Jawna konwersja jest rozważyć użycie wyrażeniem rzutowania.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="e9c9e-124">Jawne konwersje może obciąć danych lub utratę dokładności.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9c9e-125">RZUTOWANIE jest obsługiwane tylko typy pierwotne i typy wyliczeniowe elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9c9e-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9c9e-126">Example</span></span>  
 <span data-ttu-id="e9c9e-127">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora RZUTOWANIA w celu rzutowania wyrażenia jednego typu danych na inny.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="e9c9e-128">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e9c9e-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e9c9e-129">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="e9c9e-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e9c9e-130">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e9c9e-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="e9c9e-131">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="e9c9e-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="e9c9e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9c9e-132">See Also</span></span>  
 [<span data-ttu-id="e9c9e-133">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e9c9e-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

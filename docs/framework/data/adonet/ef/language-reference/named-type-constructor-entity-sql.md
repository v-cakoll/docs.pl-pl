---
title: Konstruktor typu nazwanego (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
ms.openlocfilehash: f95f0dcb92068675b2efff0af7e97b349976bf42
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329469"
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="f793c-102">Konstruktor typu nazwanego (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="f793c-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="f793c-103">Używane do tworzenia wystąpień typów nominalna modelu koncepcyjnego, takich jak jednostki lub typy złożone.</span><span class="sxs-lookup"><span data-stu-id="f793c-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f793c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f793c-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="f793c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f793c-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="f793c-106">Wartość, która jest proste lub cytowanego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="f793c-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="f793c-107">Aby uzyskać więcej informacji, zobacz [identyfikatorów](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="f793c-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="f793c-108">Atrybuty typu, które są zakłada się, że w tej samej kolejności, w jakiej występują w deklaracji typu.</span><span class="sxs-lookup"><span data-stu-id="f793c-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f793c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f793c-109">Return Value</span></span>  
 <span data-ttu-id="f793c-110">Wystąpienia elementu o nazwie typy złożone i typy jednostek.</span><span class="sxs-lookup"><span data-stu-id="f793c-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f793c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f793c-111">Remarks</span></span>  
 <span data-ttu-id="f793c-112">W poniższych przykładach pokazano sposób tworzenia nominalna i złożone typy:</span><span class="sxs-lookup"><span data-stu-id="f793c-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="f793c-113">Poniższe wyrażenie tworzy wystąpienie `Person` typu:</span><span class="sxs-lookup"><span data-stu-id="f793c-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="f793c-114">Poniższe wyrażenie tworzenia wystąpienia tego typu złożonego:</span><span class="sxs-lookup"><span data-stu-id="f793c-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="f793c-115">Poniższe wyrażenie tworzy wystąpienie klasy zagnieżdżony typ złożony:</span><span class="sxs-lookup"><span data-stu-id="f793c-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="f793c-116">Poniższe wyrażenie tworzy wystąpienie jednostki z zagnieżdżony typ złożony:</span><span class="sxs-lookup"><span data-stu-id="f793c-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="f793c-117">Poniższy przykład pokazuje, jak zainicjować właściwość typu złożonego do wartości null:`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="f793c-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="f793c-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="f793c-118">Example</span></span>  
 <span data-ttu-id="f793c-119">Następujące zapytanie SQL jednostki używa Konstruktor typu nazwanego w celu utworzenia wystąpienia typu modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="f793c-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="f793c-120">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f793c-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f793c-121">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f793c-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f793c-122">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f793c-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f793c-123">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="f793c-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="f793c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f793c-124">See also</span></span>

- [<span data-ttu-id="f793c-125">Konstruowanie typów</span><span class="sxs-lookup"><span data-stu-id="f793c-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [<span data-ttu-id="f793c-126">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f793c-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

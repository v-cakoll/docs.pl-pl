---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 40a5afd7eb99dba7cae8fe14ed0a45213fda94a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149950"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="f293c-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f293c-102">REF (Entity SQL)</span></span>
<span data-ttu-id="f293c-103">Zwraca odwołanie do wystąpienia jednostki.</span><span class="sxs-lookup"><span data-stu-id="f293c-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f293c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f293c-104">Syntax</span></span>  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a><span data-ttu-id="f293c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f293c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f293c-106">Dowolne prawidłowe wyrażenie, które daje wystąpienie typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="f293c-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f293c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f293c-107">Return Value</span></span>  
 <span data-ttu-id="f293c-108">Odwołanie do określonego wystąpienia jednostki.</span><span class="sxs-lookup"><span data-stu-id="f293c-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f293c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f293c-109">Remarks</span></span>  
 <span data-ttu-id="f293c-110">Odwołanie do jednostki składa się z klucza jednostki i nazwy zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="f293c-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="f293c-111">Ponieważ różne zestawy jednostek mogą być oparte na tym samym typie encji, klucz określonej jednostki może pojawić się w wielu zestawach jednostek.</span><span class="sxs-lookup"><span data-stu-id="f293c-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="f293c-112">Jednak odwołanie do jednostki jest zawsze unikatowe.</span><span class="sxs-lookup"><span data-stu-id="f293c-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="f293c-113">Jeśli wyrażenie wejściowe reprezentuje utrwaloną jednostkę, zostanie zwrócone odwołanie do tej jednostki.</span><span class="sxs-lookup"><span data-stu-id="f293c-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="f293c-114">Jeśli wyrażenie wejściowe nie jest utrwaloną jednostką, zostanie zwrócone odwołanie null.</span><span class="sxs-lookup"><span data-stu-id="f293c-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="f293c-115">Jeśli operator wyodrębniania właściwości (.) jest używany do uzyskiwania dostępu do właściwości jednostki, odwołanie jest automatycznie wyłuskiwane.</span><span class="sxs-lookup"><span data-stu-id="f293c-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f293c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f293c-116">Example</span></span>  
 <span data-ttu-id="f293c-117">Następująca kwerenda SQL jednostki używa operatora REF do zwrócenia odwołania dla argumentu jednostki wejściowej.</span><span class="sxs-lookup"><span data-stu-id="f293c-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="f293c-118">Ta sama kwerenda wyłuduje odwołanie, ponieważ używamy operacji wyodrębniania właściwości (.) w celu uzyskania dostępu do właściwości Product jednostki.</span><span class="sxs-lookup"><span data-stu-id="f293c-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="f293c-119">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f293c-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f293c-120">Aby skompilować i uruchomić tę kwerendę, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f293c-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f293c-121">Postępuj zgodnie z procedurą [w : Jak wykonać kwerendę, która zwraca wyniki typu pierwotnego](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f293c-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="f293c-122">Przekaż następującą kwerendę jako `ExecutePrimitiveTypeQuery` argument do metody:</span><span class="sxs-lookup"><span data-stu-id="f293c-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="f293c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f293c-123">See also</span></span>

- [<span data-ttu-id="f293c-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="f293c-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="f293c-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="f293c-125">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="f293c-126">Klucz</span><span class="sxs-lookup"><span data-stu-id="f293c-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="f293c-127">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="f293c-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f293c-128">Definicje typu</span><span class="sxs-lookup"><span data-stu-id="f293c-128">Type Definitions</span></span>](type-definitions-entity-sql.md)

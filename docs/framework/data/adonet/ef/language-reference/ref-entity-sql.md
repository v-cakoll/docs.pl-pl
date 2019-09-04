---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 9d35306d1299e91ecaa55a7d2818ee1e2982793f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249194"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="0f582-102">REF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0f582-102">REF (Entity SQL)</span></span>
<span data-ttu-id="0f582-103">Zwraca odwołanie do wystąpienia jednostki.</span><span class="sxs-lookup"><span data-stu-id="0f582-103">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f582-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f582-104">Syntax</span></span>  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a><span data-ttu-id="0f582-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0f582-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0f582-106">Dowolne prawidłowe wyrażenie zwracające wystąpienie typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="0f582-106">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f582-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0f582-107">Return Value</span></span>  
 <span data-ttu-id="0f582-108">Odwołanie do określonego wystąpienia jednostki.</span><span class="sxs-lookup"><span data-stu-id="0f582-108">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f582-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f582-109">Remarks</span></span>  
 <span data-ttu-id="0f582-110">Odwołanie do jednostki składa się z klucza jednostki i nazwy zestawu jednostek.</span><span class="sxs-lookup"><span data-stu-id="0f582-110">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="0f582-111">Ponieważ różne zestawy jednostek mogą opierać się na tym samym typie jednostki, określony klucz jednostki może pojawić się w wielu zestawach jednostek.</span><span class="sxs-lookup"><span data-stu-id="0f582-111">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="0f582-112">Odwołanie do jednostki jest jednak zawsze unikatowe.</span><span class="sxs-lookup"><span data-stu-id="0f582-112">However, an entity reference is always unique.</span></span> <span data-ttu-id="0f582-113">Jeśli wyrażenie danych wejściowych reprezentuje obiekt utrwalony, odwołanie do tej jednostki zostanie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="0f582-113">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="0f582-114">Jeśli wyrażenie wejściowe nie jest utrwaloną jednostką, zostanie zwrócone odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="0f582-114">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="0f582-115">Jeśli operator wyodrębniania właściwości (.) jest używany w celu uzyskania dostępu do właściwości jednostki, odwołanie zostanie automatycznie wywoływać.</span><span class="sxs-lookup"><span data-stu-id="0f582-115">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f582-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f582-116">Example</span></span>  
 <span data-ttu-id="0f582-117">Poniższe zapytanie Entity SQL używa operatora REF do zwrócenia odwołania dla argumentu jednostki wejściowej.</span><span class="sxs-lookup"><span data-stu-id="0f582-117">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="0f582-118">To samo zapytanie odwołuje się do odwołania, ponieważ używamy operacji wyodrębniania właściwości (.) w celu uzyskania dostępu do właściwości jednostki produktu.</span><span class="sxs-lookup"><span data-stu-id="0f582-118">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="0f582-119">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0f582-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0f582-120">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="0f582-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0f582-121">Wykonaj czynności opisane w [temacie How to: Wykonaj zapytanie zwracające wyniki](../how-to-execute-a-query-that-returns-primitivetype-results.md)typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="0f582-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="0f582-122">Przekaż następujące zapytanie jako argument do `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="0f582-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="0f582-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f582-123">See also</span></span>

- [<span data-ttu-id="0f582-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="0f582-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="0f582-125">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="0f582-125">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="0f582-126">KEY</span><span class="sxs-lookup"><span data-stu-id="0f582-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="0f582-127">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="0f582-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="0f582-128">Definicje typu</span><span class="sxs-lookup"><span data-stu-id="0f582-128">Type Definitions</span></span>](type-definitions-entity-sql.md)

---
title: KOLEKCJA (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: d4e52bb62412e61e1a71e0fe9a8555068ca18dbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506462"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="13e7a-102">KOLEKCJA (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="13e7a-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="13e7a-103">KOLEKCJA — słowo kluczowe jest używane tylko w definicji wbudowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="13e7a-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="13e7a-104">Funkcje kolekcji są funkcje, które działają na zbiór wartości, a następnie generuje skalarne danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="13e7a-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e7a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="13e7a-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="13e7a-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="13e7a-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="13e7a-107">Wyrażenie, które zwraca kolekcję obsługiwanych typów, wiersze lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="13e7a-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13e7a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13e7a-108">Remarks</span></span>  
 <span data-ttu-id="13e7a-109">Aby uzyskać więcej informacji na temat KOLEKCJI — słowo kluczowe zobacz [definicje typów](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="13e7a-109">For more information about the COLLECTION keyword, see [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13e7a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="13e7a-110">Example</span></span>  
 <span data-ttu-id="13e7a-111">Poniższy przykład pokazuje sposób użycia KOLEKCJI — słowo kluczowe do deklarowania kolekcję jako argument wbudowanej funkcji zapytania liczbę miejsc dziesiętnych.</span><span class="sxs-lookup"><span data-stu-id="13e7a-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="13e7a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13e7a-112">See also</span></span>
- [<span data-ttu-id="13e7a-113">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="13e7a-113">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

---
title: . (Dostęp do elementów członkowskich) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 8e63caba9e9efb91d5c4629b9da0b1feca905ace
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319650"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="37cc9-103">.</span><span class="sxs-lookup"><span data-stu-id="37cc9-103">.</span></span> <span data-ttu-id="37cc9-104">(Dostęp do elementów członkowskich) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="37cc9-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="37cc9-105">Operator kropki (.) to operator dostępu do składowej [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="37cc9-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="37cc9-106">Operator dostępu do elementu członkowskiego jest używany do uzyskania wartości właściwości lub pola wystąpienia typu modelu koncepcyjnego koncepcyjny.</span><span class="sxs-lookup"><span data-stu-id="37cc9-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37cc9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="37cc9-107">Syntax</span></span>  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="37cc9-108">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37cc9-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="37cc9-109">Wystąpienie strukturalnego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="37cc9-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="37cc9-110">Właściwość lub pole, które należy do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="37cc9-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37cc9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37cc9-111">Remarks</span></span>  
 <span data-ttu-id="37cc9-112">Operator kropki (.) może służyć do wyodrębniania pól z rekordu, podobnie jak w przypadku wyodrębniania właściwości typu złożonego lub jednostki.</span><span class="sxs-lookup"><span data-stu-id="37cc9-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="37cc9-113">Na przykład jeśli n typu nazwa jest członkiem typu osoba, a p jest wystąpieniem typu Person, a p. n jest dozwolonym wyrażeniem dostępu do elementu członkowskiego, który zwraca wartość typu Name.</span><span class="sxs-lookup"><span data-stu-id="37cc9-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="37cc9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37cc9-114">See also</span></span>

- [<span data-ttu-id="37cc9-115">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="37cc9-115">Entity SQL Reference</span></span>](entity-sql-reference.md)

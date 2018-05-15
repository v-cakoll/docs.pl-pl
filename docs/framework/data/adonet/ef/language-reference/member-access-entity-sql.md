---
title: . (Dostęp do elementu członkowskiego) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: fdcd026d245b3f6d6ecaccc0f828f3d77fd6ce1a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="b0247-103">.</span><span class="sxs-lookup"><span data-stu-id="b0247-103">.</span></span> <span data-ttu-id="b0247-104">(Dostęp do elementu członkowskiego) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="b0247-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="b0247-105">Operator kropki (.) jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatora dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b0247-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="b0247-106">Operator dostępu do elementu członkowskiego umożliwia uzyskanie wartość właściwości lub pola wystąpienia typu strukturalnego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="b0247-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0247-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0247-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="b0247-108">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b0247-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b0247-109">Wystąpienie typu strukturalnego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="b0247-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="b0247-110">Właściwości lub pola należącego do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="b0247-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0247-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0247-111">Remarks</span></span>  
 <span data-ttu-id="b0247-112">Operator kropki (.) może służyć do wyodrębniania pól z rekordu, podobnie jak Wyodrębnianie właściwości typu złożonych lub jednostki.</span><span class="sxs-lookup"><span data-stu-id="b0247-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="b0247-113">Na przykład jeśli n Nazwa typu jest elementem członkowskim typu osoby i p jest wystąpieniem typu osoby, p.n jest wyrażenie dostępu elementu członkowskiego prawnych, zwracające wartość wpisz nazwę.</span><span class="sxs-lookup"><span data-stu-id="b0247-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="b0247-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0247-114">See Also</span></span>  
 [<span data-ttu-id="b0247-115">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="b0247-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

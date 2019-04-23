---
title: . (Dostęp do elementu członkowskiego) (Jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 6ebedd2b381d035d199e151f64632acf7d502ff5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139714"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="3e481-103">.</span><span class="sxs-lookup"><span data-stu-id="3e481-103">.</span></span> <span data-ttu-id="3e481-104">(Dostęp do elementu członkowskiego) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="3e481-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="3e481-105">Operator kropki (.) jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operator dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3e481-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="3e481-106">Operator dostępu do elementu członkowskiego umożliwia uzyskanie wartość właściwość lub pole wystąpienia typu modelu koncepcyjnego strukturalnych.</span><span class="sxs-lookup"><span data-stu-id="3e481-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e481-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e481-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e481-108">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3e481-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3e481-109">Wystąpienie typu modelu koncepcyjnego strukturalnych.</span><span class="sxs-lookup"><span data-stu-id="3e481-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="3e481-110">Właściwość lub pole, które należy do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3e481-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e481-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e481-111">Remarks</span></span>  
 <span data-ttu-id="3e481-112">Operator kropki (.) może służyć do wyodrębniania pól z rekordu, podobnie jak Wyodrębnianie właściwości typu złożonych lub jednostki.</span><span class="sxs-lookup"><span data-stu-id="3e481-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="3e481-113">Na przykład jeśli n Nazwa typu jest elementem członkowskim typu osoby i p jest wystąpieniem typu osoby, p.n jest wyrażenia dostępu do elementu członkowskiego prawne, której wynikiem jest wartość typu nazwy.</span><span class="sxs-lookup"><span data-stu-id="3e481-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="3e481-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e481-114">See also</span></span>

- [<span data-ttu-id="3e481-115">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3e481-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

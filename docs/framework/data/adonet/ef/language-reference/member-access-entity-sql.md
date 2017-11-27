---
title: ". (Dostęp do elementu członkowskiego) (Jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c9d5d8f2c90273b316379d3c2803835bab3faef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="73767-103">.</span><span class="sxs-lookup"><span data-stu-id="73767-103">.</span></span> <span data-ttu-id="73767-104">(Dostęp do elementu członkowskiego) (Jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="73767-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="73767-105">Operator kropki (.) jest [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operatora dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="73767-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="73767-106">Operator dostępu do elementu członkowskiego umożliwia uzyskanie wartość właściwości lub pola wystąpienia typu strukturalnego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="73767-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73767-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="73767-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="73767-108">Argumenty</span><span class="sxs-lookup"><span data-stu-id="73767-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="73767-109">Wystąpienie typu strukturalnego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="73767-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="73767-110">Właściwości lub pola należącego do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="73767-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73767-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73767-111">Remarks</span></span>  
 <span data-ttu-id="73767-112">Operator kropki (.) może służyć do wyodrębniania pól z rekordu, podobnie jak Wyodrębnianie właściwości typu złożonych lub jednostki.</span><span class="sxs-lookup"><span data-stu-id="73767-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="73767-113">Na przykład jeśli n Nazwa typu jest elementem członkowskim typu osoby i p jest wystąpieniem typu osoby, p.n jest wyrażenie dostępu elementu członkowskiego prawnych, zwracające wartość wpisz nazwę.</span><span class="sxs-lookup"><span data-stu-id="73767-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="73767-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73767-114">See Also</span></span>  
 [<span data-ttu-id="73767-115">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="73767-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

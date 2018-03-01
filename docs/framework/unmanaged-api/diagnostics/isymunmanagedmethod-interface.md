---
title: "ISymUnmanagedMethod — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b6305625c3d02dbd126a284287e19b319e21eeba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="251eb-102">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="251eb-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="251eb-103">Reprezentuje metodę w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="251eb-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="251eb-104">Ten interfejs umożliwia dostęp do tylko powiązane symbol atrybuty metody, zamiast atrybutów związanych z typu.</span><span class="sxs-lookup"><span data-stu-id="251eb-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="251eb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="251eb-105">Methods</span></span>  
  
|<span data-ttu-id="251eb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-106">Method</span></span>|<span data-ttu-id="251eb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="251eb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="251eb-108">GetNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="251eb-109">Pobiera obszar nazw, w którym ta metoda jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="251eb-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="251eb-110">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="251eb-111">Zwraca przesunięcie w ramach tej metody, która odpowiada na określonej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="251eb-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="251eb-112">GetParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="251eb-113">Pobiera parametry dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="251eb-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="251eb-114">GetRanges, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="251eb-115">Podanej pozycji w dokumencie zwraca tablicę początkową i końcową pary przesunięcia, które odpowiadają zakresom język pośredni firmy Microsoft (MSIL), który obejmuje pozycję w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="251eb-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="251eb-116">GetRootScope, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="251eb-117">Pobiera zakres leksykalne głównego w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="251eb-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="251eb-118">Ten zakres obejmuje całą metody.</span><span class="sxs-lookup"><span data-stu-id="251eb-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="251eb-119">GetScopeFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="251eb-120">Pobiera najbardziej otaczającym zakresie leksykalne w ramach tej metody, które umieszcza danego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="251eb-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="251eb-121">GetSequencePointCount, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="251eb-122">Pobiera liczbę punktów sekwencji w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="251eb-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="251eb-123">GetSequencePoints, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="251eb-124">Pobiera wszystkie punkty sekwencji w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="251eb-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="251eb-125">GetSourceStartEnd, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="251eb-126">Pobiera dokument pozycje początkowe i końcowe dla źródła tej metody.</span><span class="sxs-lookup"><span data-stu-id="251eb-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="251eb-127">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="251eb-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="251eb-128">Zwraca token metadanych dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="251eb-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="251eb-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="251eb-129">Requirements</span></span>  
 <span data-ttu-id="251eb-130">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="251eb-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251eb-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="251eb-131">See Also</span></span>  
 [<span data-ttu-id="251eb-132">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="251eb-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)

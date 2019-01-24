---
title: ISymUnmanagedMethod — Interfejs
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b19e5ce88ea34188b2757d2a0c313341fbf1e7e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604265"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="c41bb-102">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c41bb-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="c41bb-103">Reprezentuje metodę w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="c41bb-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="c41bb-104">Ten interfejs zapewnia dostęp do tylko powiązane symbol atrybuty metody, zamiast atrybutów związane z typu.</span><span class="sxs-lookup"><span data-stu-id="c41bb-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c41bb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c41bb-105">Methods</span></span>  
  
|<span data-ttu-id="c41bb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-106">Method</span></span>|<span data-ttu-id="c41bb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c41bb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c41bb-108">GetNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="c41bb-109">Pobiera obszar nazw, w którym ta metoda jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="c41bb-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="c41bb-110">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="c41bb-111">Zwraca przesunięcie w ramach tej metody, która odnosi się do określonej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="c41bb-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="c41bb-112">GetParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="c41bb-113">Pobiera parametry dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="c41bb-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="c41bb-114">GetRanges, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="c41bb-115">Danou pozici w dokumencie zwraca tablicę rozpoczęcia i zakończenia pary przesunięcia, które odnoszą się do zakresów języka Microsoft intermediate language (MSIL) uwzględniającą pozycja w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="c41bb-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="c41bb-116">GetRootScope, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="c41bb-117">Pobiera zakres leksykalne głównego w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="c41bb-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="c41bb-118">Ten zakres obejmuje całą metodę.</span><span class="sxs-lookup"><span data-stu-id="c41bb-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="c41bb-119">GetScopeFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="c41bb-120">Pobiera najbardziej otaczającym zakresie leksykalnym w ramach tej metody, która otacza danego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="c41bb-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="c41bb-121">GetSequencePointCount, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="c41bb-122">Pobiera liczbę punktów sekwencji w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="c41bb-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="c41bb-123">GetSequencePoints, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="c41bb-124">Pobiera wszystkie punkty sekwencji w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="c41bb-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="c41bb-125">GetSourceStartEnd, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="c41bb-126">Pobiera położenie dokumentu rozpoczęcia i zakończenia dla źródłowej, tej metody.</span><span class="sxs-lookup"><span data-stu-id="c41bb-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="c41bb-127">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="c41bb-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="c41bb-128">Zwraca token metadanych dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="c41bb-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c41bb-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c41bb-129">Requirements</span></span>  
 <span data-ttu-id="c41bb-130">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c41bb-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41bb-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c41bb-131">See also</span></span>
- [<span data-ttu-id="c41bb-132">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="c41bb-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)

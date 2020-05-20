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
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615127"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="0f56b-102">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0f56b-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="0f56b-103">Reprezentuje metodę w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="0f56b-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="0f56b-104">Ten interfejs zapewnia dostęp tylko do atrybutów związanych z symbolami metody, a nie atrybutów związanych z typem.</span><span class="sxs-lookup"><span data-stu-id="0f56b-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f56b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0f56b-105">Methods</span></span>  
  
|<span data-ttu-id="0f56b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-106">Method</span></span>|<span data-ttu-id="0f56b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0f56b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f56b-108">GetNamespace, metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-108">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="0f56b-109">Pobiera przestrzeń nazw, w której jest zdefiniowana ta metoda.</span><span class="sxs-lookup"><span data-stu-id="0f56b-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="0f56b-110">GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-110">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="0f56b-111">Zwraca przesunięcie w ramach tej metody, które odnosi się do danej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="0f56b-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="0f56b-112">GetParameters, metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-112">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="0f56b-113">Pobiera parametry dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="0f56b-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="0f56b-114">GetRanges, metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-114">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="0f56b-115">Nadana pozycja w dokumencie zwraca tablicę par przesunięć początkowych i końcowych odpowiadających zakresom języka pośredniego firmy Microsoft (MSIL), który znajduje się w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="0f56b-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="0f56b-116">GetRootScope, metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-116">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="0f56b-117">Pobiera zakres leksykalny głównej w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="0f56b-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="0f56b-118">Ten zakres obejmuje całą metodę.</span><span class="sxs-lookup"><span data-stu-id="0f56b-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="0f56b-119">GetScopeFromOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-119">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="0f56b-120">Pobiera najbardziej otaczający zakres leksykalny w ramach tej metody, który obejmuje określone przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="0f56b-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="0f56b-121">GetSequencePointCount, metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-121">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="0f56b-122">Pobiera liczbę punktów sekwencji w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="0f56b-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="0f56b-123">GetSequencePoints, metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-123">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="0f56b-124">Pobiera wszystkie punkty sekwencji w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="0f56b-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="0f56b-125">GetSourceStartEnd, metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-125">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="0f56b-126">Pobiera położenie początku i końca dokumentu dla źródła tej metody.</span><span class="sxs-lookup"><span data-stu-id="0f56b-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="0f56b-127">GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f56b-127">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="0f56b-128">Zwraca token metadanych dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="0f56b-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f56b-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f56b-129">Requirements</span></span>  
 <span data-ttu-id="0f56b-130">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0f56b-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f56b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f56b-131">See also</span></span>

- [<span data-ttu-id="0f56b-132">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="0f56b-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)

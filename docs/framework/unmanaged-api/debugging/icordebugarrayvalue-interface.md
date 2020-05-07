---
title: ICorDebugArrayValue, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: bd1e86b83c43af20604416f158ab9e74f399821b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894970"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="588e9-102">ICorDebugArrayValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="588e9-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="588e9-103">Podklasa elementu ICorDebugHeapValue, która reprezentuje tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="588e9-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="588e9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="588e9-104">Methods</span></span>  
  
|<span data-ttu-id="588e9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-105">Method</span></span>|<span data-ttu-id="588e9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="588e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="588e9-107">GetBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-107">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="588e9-108">Pobiera podstawowy indeks każdego wymiaru w tablicy.</span><span class="sxs-lookup"><span data-stu-id="588e9-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="588e9-109">GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-109">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="588e9-110">Pobiera łączną liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="588e9-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="588e9-111">GetDimensions, metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-111">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="588e9-112">Pobiera Wymiary tablicy.</span><span class="sxs-lookup"><span data-stu-id="588e9-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="588e9-113">GetElement, metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-113">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="588e9-114">Pobiera wartość reprezentującą dany element w tablicy.</span><span class="sxs-lookup"><span data-stu-id="588e9-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="588e9-115">GetElementAtPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-115">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="588e9-116">Pobiera element w podanym miejscu, traktując tablicę jako tablicę jednowymiarową o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="588e9-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="588e9-117">GetElementType, metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-117">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="588e9-118">Pobiera prosty typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="588e9-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="588e9-119">GetRank — Metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-119">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="588e9-120">Pobiera liczbę wymiarów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="588e9-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="588e9-121">HasBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="588e9-121">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="588e9-122">Określa, czy tablica ma indeksy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="588e9-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="588e9-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="588e9-123">Remarks</span></span>  
 <span data-ttu-id="588e9-124">`ICorDebugArrayValue`obsługuje tablice jednowymiarowe i wielowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="588e9-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="588e9-125">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="588e9-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="588e9-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="588e9-126">Requirements</span></span>  
 <span data-ttu-id="588e9-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="588e9-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="588e9-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="588e9-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="588e9-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="588e9-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="588e9-130">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="588e9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="588e9-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="588e9-131">See also</span></span>

- [<span data-ttu-id="588e9-132">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="588e9-132">Debugging Interfaces</span></span>](debugging-interfaces.md)

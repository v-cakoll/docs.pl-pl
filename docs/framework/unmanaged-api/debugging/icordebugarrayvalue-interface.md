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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99bd3e9ae1faec1b71933681fadf4816b4789c98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952212"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="d4da4-102">ICorDebugArrayValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4da4-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="d4da4-103">Podklasa elementu ICorDebugHeapValue, która reprezentuje tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="d4da4-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4da4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d4da4-104">Methods</span></span>  
  
|<span data-ttu-id="d4da4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-105">Method</span></span>|<span data-ttu-id="d4da4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d4da4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4da4-107">GetBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="d4da4-108">Pobiera podstawowy indeks każdego wymiaru w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4da4-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="d4da4-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="d4da4-110">Pobiera łączną liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4da4-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="d4da4-111">GetDimensions, metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="d4da4-112">Pobiera Wymiary tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4da4-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="d4da4-113">GetElement, metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="d4da4-114">Pobiera wartość reprezentującą dany element w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4da4-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="d4da4-115">GetElementAtPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="d4da4-116">Pobiera element w podanym miejscu, traktując tablicę jako tablicę jednowymiarową o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="d4da4-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="d4da4-117">GetElementType, metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="d4da4-118">Pobiera prosty typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4da4-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="d4da4-119">GetRank, metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="d4da4-120">Pobiera liczbę wymiarów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d4da4-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="d4da4-121">HasBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="d4da4-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="d4da4-122">Określa, czy tablica ma indeksy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="d4da4-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4da4-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4da4-123">Remarks</span></span>  
 <span data-ttu-id="d4da4-124">`ICorDebugArrayValue`obsługuje tablice jednowymiarowe i wielowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="d4da4-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4da4-125">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="d4da4-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4da4-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4da4-126">Requirements</span></span>  
 <span data-ttu-id="d4da4-127">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4da4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4da4-128">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4da4-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4da4-129">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4da4-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4da4-130">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4da4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4da4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4da4-131">See also</span></span>

- [<span data-ttu-id="d4da4-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d4da4-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

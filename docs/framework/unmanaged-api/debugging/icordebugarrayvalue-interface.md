---
title: ICorDebugArrayValue — Interfejs
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
ms.openlocfilehash: e41bb5ca0fdd999692395239304f50a6f745a4f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088271"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="4526e-102">ICorDebugArrayValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4526e-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="4526e-103">Podklasa elementu ICorDebugHeapValue, która reprezentuje tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="4526e-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4526e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4526e-104">Methods</span></span>  
  
|<span data-ttu-id="4526e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-105">Method</span></span>|<span data-ttu-id="4526e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4526e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4526e-107">GetBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="4526e-108">Pobiera podstawowy indeks każdego wymiaru w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4526e-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="4526e-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="4526e-110">Pobiera łączną liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4526e-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="4526e-111">GetDimensions, metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="4526e-112">Pobiera Wymiary tablicy.</span><span class="sxs-lookup"><span data-stu-id="4526e-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="4526e-113">GetElement, metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="4526e-114">Pobiera wartość reprezentującą dany element w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4526e-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="4526e-115">GetElementAtPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="4526e-116">Pobiera element w podanym miejscu, traktując tablicę jako tablicę jednowymiarową o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="4526e-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="4526e-117">GetElementType, metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="4526e-118">Pobiera prosty typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4526e-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="4526e-119">GetRank, metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="4526e-120">Pobiera liczbę wymiarów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4526e-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="4526e-121">HasBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="4526e-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="4526e-122">Określa, czy tablica ma indeksy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="4526e-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4526e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4526e-123">Remarks</span></span>  
 <span data-ttu-id="4526e-124">`ICorDebugArrayValue` obsługuje tablice jednowymiarowe i wielowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="4526e-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4526e-125">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="4526e-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4526e-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4526e-126">Requirements</span></span>  
 <span data-ttu-id="4526e-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4526e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4526e-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4526e-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4526e-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4526e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4526e-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4526e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4526e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4526e-131">See also</span></span>

- [<span data-ttu-id="4526e-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4526e-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

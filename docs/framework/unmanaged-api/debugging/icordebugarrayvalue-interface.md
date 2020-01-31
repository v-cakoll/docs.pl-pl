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
ms.openlocfilehash: 0944f3379c18cba56ab65fe40a5b94a64d8a8991
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778201"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="cb5ff-102">ICorDebugArrayValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb5ff-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="cb5ff-103">Podklasa elementu ICorDebugHeapValue, która reprezentuje tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb5ff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cb5ff-104">Methods</span></span>  
  
|<span data-ttu-id="cb5ff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-105">Method</span></span>|<span data-ttu-id="cb5ff-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cb5ff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb5ff-107">GetBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-107">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="cb5ff-108">Pobiera podstawowy indeks każdego wymiaru w tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="cb5ff-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-109">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="cb5ff-110">Pobiera łączną liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="cb5ff-111">GetDimensions, metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-111">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="cb5ff-112">Pobiera Wymiary tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="cb5ff-113">GetElement, metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-113">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="cb5ff-114">Pobiera wartość reprezentującą dany element w tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="cb5ff-115">GetElementAtPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-115">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="cb5ff-116">Pobiera element w podanym miejscu, traktując tablicę jako tablicę jednowymiarową o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="cb5ff-117">GetElementType, metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-117">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="cb5ff-118">Pobiera prosty typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="cb5ff-119">GetRank, metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-119">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="cb5ff-120">Pobiera liczbę wymiarów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="cb5ff-121">HasBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ff-121">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="cb5ff-122">Określa, czy tablica ma indeksy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb5ff-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb5ff-123">Remarks</span></span>  
 <span data-ttu-id="cb5ff-124">`ICorDebugArrayValue` obsługuje tablice jednowymiarowe i wielowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb5ff-125">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="cb5ff-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5ff-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb5ff-126">Requirements</span></span>  
 <span data-ttu-id="cb5ff-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb5ff-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5ff-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb5ff-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb5ff-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cb5ff-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb5ff-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5ff-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5ff-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb5ff-131">See also</span></span>

- [<span data-ttu-id="cb5ff-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cb5ff-132">Debugging Interfaces</span></span>](debugging-interfaces.md)

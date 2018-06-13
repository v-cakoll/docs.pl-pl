---
title: ICorDebugArrayValue Interface1
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
ms.openlocfilehash: a96f2b21e524f03ea3290be268244eaceeb5c7f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408180"
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="a4c11-102">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="a4c11-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="a4c11-103">Podklasa ICorDebugHeapValue reprezentujący tablicy jednowymiarowej lub wielowymiarowych.</span><span class="sxs-lookup"><span data-stu-id="a4c11-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4c11-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a4c11-104">Methods</span></span>  
  
|<span data-ttu-id="a4c11-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-105">Method</span></span>|<span data-ttu-id="a4c11-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a4c11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4c11-107">GetBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="a4c11-108">Pobiera podstawowy indeks każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="a4c11-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="a4c11-110">Pobiera całkowitą liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="a4c11-111">GetDimensions, metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="a4c11-112">Pobiera wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="a4c11-113">GetElement, metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="a4c11-114">Pobiera wartość reprezentującą danego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="a4c11-115">GetElementAtPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="a4c11-116">Pobiera element na pozycji, traktując jako tablica liczony od zera, jednowymiarowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="a4c11-117">GetElementType, metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="a4c11-118">Pobiera prosty typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="a4c11-119">GetRank, metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="a4c11-120">Pobiera liczbę wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="a4c11-121">HasBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="a4c11-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="a4c11-122">Określa, czy tablica zawiera podstawowe indeksy.</span><span class="sxs-lookup"><span data-stu-id="a4c11-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4c11-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4c11-123">Remarks</span></span>  
 <span data-ttu-id="a4c11-124">`ICorDebugArrayValue` obsługuje zarówno jednowymiarowe i wielowymiarowych tablic.</span><span class="sxs-lookup"><span data-stu-id="a4c11-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4c11-125">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="a4c11-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c11-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4c11-126">Requirements</span></span>  
 <span data-ttu-id="a4c11-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4c11-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c11-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4c11-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4c11-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4c11-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4c11-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c11-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c11-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4c11-131">See Also</span></span>  
 [<span data-ttu-id="a4c11-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a4c11-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

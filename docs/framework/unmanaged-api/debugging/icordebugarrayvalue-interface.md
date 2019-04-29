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
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645620"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="a4947-102">ICorDebugArrayValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="a4947-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="a4947-103">Podklasa klasy ICorDebugHeapValue, który reprezentuje tablicę jednowymiarową lub wielowymiarową.</span><span class="sxs-lookup"><span data-stu-id="a4947-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4947-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a4947-104">Methods</span></span>  
  
|<span data-ttu-id="a4947-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-105">Method</span></span>|<span data-ttu-id="a4947-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a4947-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4947-107">GetBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="a4947-108">Pobiera podstawowy indeks każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4947-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="a4947-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="a4947-110">Pobiera całkowitą liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4947-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="a4947-111">GetDimensions, metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="a4947-112">Pobiera wymiary tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4947-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="a4947-113">GetElement, metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="a4947-114">Pobiera wartość reprezentującą danego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4947-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="a4947-115">GetElementAtPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="a4947-116">Pobiera element wskazywany danej pozycji, traktując tablicy jako tablicę indeksowaną od zera, jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="a4947-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="a4947-117">GetElementType, metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="a4947-118">Pobiera prosty typ elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4947-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="a4947-119">GetRank, metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="a4947-120">Pobiera liczbę wymiarów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4947-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="a4947-121">HasBaseIndicies, metoda</span><span class="sxs-lookup"><span data-stu-id="a4947-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="a4947-122">Określa, czy tablica zawiera indeksy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="a4947-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4947-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4947-123">Remarks</span></span>  
 <span data-ttu-id="a4947-124">`ICorDebugArrayValue` obsługuje tablice jednowymiarowe i wielowymiarowe.</span><span class="sxs-lookup"><span data-stu-id="a4947-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4947-125">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="a4947-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4947-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4947-126">Requirements</span></span>  
 <span data-ttu-id="a4947-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4947-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4947-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4947-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4947-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4947-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4947-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4947-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4947-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4947-131">See also</span></span>

- [<span data-ttu-id="a4947-132">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a4947-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

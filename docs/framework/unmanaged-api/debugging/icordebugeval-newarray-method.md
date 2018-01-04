---
title: "ICorDebugEval::NewArray — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9116c2ee7edbc39d203728909ce37e963c896fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="5e5df-102">ICorDebugEval::NewArray — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e5df-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="5e5df-103">Przydziela nowej tablicy o typie określonym elemencie i wymiary.</span><span class="sxs-lookup"><span data-stu-id="5e5df-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="5e5df-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="5e5df-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5e5df-105">Użyj [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5e5df-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e5df-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e5df-106">Syntax</span></span>  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e5df-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e5df-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="5e5df-108">[in] Wartość wyliczenia CorElementType, która określa typ elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="5e5df-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="5e5df-109">[in] Wskaźnik do obiektu ICorDebugClass, który określa klasę elementu.</span><span class="sxs-lookup"><span data-stu-id="5e5df-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="5e5df-110">Ta wartość może mieć wartości zerowej, jeśli typ elementu jest typem pierwotnym.</span><span class="sxs-lookup"><span data-stu-id="5e5df-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="5e5df-111">[in] Liczba wymiarów tablicy.</span><span class="sxs-lookup"><span data-stu-id="5e5df-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="5e5df-112">W .NET Framework 2.0 ta wartość musi wynosić 1.</span><span class="sxs-lookup"><span data-stu-id="5e5df-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="5e5df-113">[in] Rozmiar w bajtach każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="5e5df-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="5e5df-114">[in] Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5e5df-114">[in] Optional.</span></span> <span data-ttu-id="5e5df-115">Dolną granicę każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="5e5df-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="5e5df-116">W przypadku pominięcia tej wartości dolna granica zero zakłada, że dla każdego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="5e5df-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e5df-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e5df-117">Remarks</span></span>  
 <span data-ttu-id="5e5df-118">Tablicy zawsze jest tworzony w domenie aplikacji, w którym wątek jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="5e5df-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e5df-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e5df-119">Requirements</span></span>  
 <span data-ttu-id="5e5df-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e5df-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e5df-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e5df-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e5df-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e5df-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e5df-123">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="5e5df-123">**.NET Framework Versions:** 1.1, 1.0</span></span>

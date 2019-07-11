---
title: ICorDebugNativeFrame2::GetStackParameterSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a5f0f767a7057064e285bf6ac9dcefc86eb9d79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757205"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="94030-102">ICorDebugNativeFrame2::GetStackParameterSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="94030-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="94030-103">Zwraca całkowity rozmiar wszystkich parametrów na stosie na x86 systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="94030-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94030-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94030-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="94030-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94030-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="94030-106">[out] Wskaźnik łącznemu rozmiarowi parametrów na stosie.</span><span class="sxs-lookup"><span data-stu-id="94030-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94030-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="94030-107">Return Value</span></span>  
 <span data-ttu-id="94030-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="94030-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="94030-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94030-109">HRESULT</span></span>|<span data-ttu-id="94030-110">Opis</span><span class="sxs-lookup"><span data-stu-id="94030-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94030-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="94030-111">S_OK</span></span>|<span data-ttu-id="94030-112">Rozmiar stosu została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="94030-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="94030-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="94030-113">S_FALSE</span></span>|<span data-ttu-id="94030-114">`GetStackParameterSize` została wywołana na platformy inne niż x86.</span><span class="sxs-lookup"><span data-stu-id="94030-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="94030-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94030-115">E_FAIL</span></span>|<span data-ttu-id="94030-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="94030-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="94030-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="94030-117">E_INVALIDARG</span></span>|<span data-ttu-id="94030-118">`pSize` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="94030-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="94030-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="94030-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94030-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94030-120">Remarks</span></span>  
 <span data-ttu-id="94030-121">[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) metody nie ustawiaj wskaźnik stosu dla parametrów, które są przekazywane na stosie.</span><span class="sxs-lookup"><span data-stu-id="94030-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="94030-122">Zamiast tego można użyć wartości zwracanej przez `GetStackParameterSize` dostosowania wskaźnik stosu do umieszczenia unwinder natywne, które dostosowanie parametrów.</span><span class="sxs-lookup"><span data-stu-id="94030-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94030-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94030-123">Requirements</span></span>  
 <span data-ttu-id="94030-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94030-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94030-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94030-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94030-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94030-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94030-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94030-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94030-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94030-128">See also</span></span>

- [<span data-ttu-id="94030-129">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="94030-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="94030-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="94030-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="94030-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="94030-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

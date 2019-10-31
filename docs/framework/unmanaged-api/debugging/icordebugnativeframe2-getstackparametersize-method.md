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
ms.openlocfilehash: 4dd9760c347bbc23f3e8225c1ff748c6b7b8bfe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096536"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="2414e-102">ICorDebugNativeFrame2::GetStackParameterSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="2414e-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="2414e-103">Zwraca skumulowany rozmiar parametrów na stosie w systemach operacyjnych x86.</span><span class="sxs-lookup"><span data-stu-id="2414e-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2414e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2414e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="2414e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2414e-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="2414e-106">określoną Wskaźnik do skumulowanego rozmiaru parametrów na stosie.</span><span class="sxs-lookup"><span data-stu-id="2414e-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2414e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2414e-107">Return Value</span></span>  
 <span data-ttu-id="2414e-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="2414e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2414e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2414e-109">HRESULT</span></span>|<span data-ttu-id="2414e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2414e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2414e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2414e-111">S_OK</span></span>|<span data-ttu-id="2414e-112">Rozmiar stosu został pomyślnie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="2414e-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="2414e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2414e-113">S_FALSE</span></span>|<span data-ttu-id="2414e-114">`GetStackParameterSize` został wywołany na platformie innej niż x86.</span><span class="sxs-lookup"><span data-stu-id="2414e-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="2414e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2414e-115">E_FAIL</span></span>|<span data-ttu-id="2414e-116">`The size of the parameters could not be returned`.,</span><span class="sxs-lookup"><span data-stu-id="2414e-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="2414e-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2414e-117">E_INVALIDARG</span></span>|<span data-ttu-id="2414e-118">`pSize` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="2414e-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2414e-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="2414e-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2414e-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2414e-120">Remarks</span></span>  
 <span data-ttu-id="2414e-121">Metody [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nie dostosowują wskaźnika stosu dla parametrów, które są wypychane na stosie.</span><span class="sxs-lookup"><span data-stu-id="2414e-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="2414e-122">Zamiast tego można użyć wartości zwracanej przez `GetStackParameterSize`, aby dostosować Wskaźnik stosu do inicjatora natywnego, który dostosowuje parametry.</span><span class="sxs-lookup"><span data-stu-id="2414e-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2414e-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2414e-123">Requirements</span></span>  
 <span data-ttu-id="2414e-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2414e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2414e-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2414e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2414e-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2414e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2414e-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2414e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2414e-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2414e-128">See also</span></span>

- [<span data-ttu-id="2414e-129">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2414e-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="2414e-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2414e-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2414e-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2414e-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

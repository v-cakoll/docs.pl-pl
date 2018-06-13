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
ms.openlocfilehash: 76ff2e502859bff27ee29a280e0d247ca1bbf1e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419559"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="0f09b-102">ICorDebugNativeFrame2::GetStackParameterSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f09b-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="0f09b-103">Zwraca całkowity rozmiar wszystkich parametrów na stosie na x86 systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="0f09b-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f09b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f09b-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f09b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f09b-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="0f09b-106">[out] Wskaźnik do całkowity rozmiar wszystkich parametrów na stosie.</span><span class="sxs-lookup"><span data-stu-id="0f09b-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f09b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0f09b-107">Return Value</span></span>  
 <span data-ttu-id="0f09b-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="0f09b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0f09b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f09b-109">HRESULT</span></span>|<span data-ttu-id="0f09b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0f09b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f09b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f09b-111">S_OK</span></span>|<span data-ttu-id="0f09b-112">Pomyślnie zwrócono rozmiar stosu.</span><span class="sxs-lookup"><span data-stu-id="0f09b-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="0f09b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0f09b-113">S_FALSE</span></span>|<span data-ttu-id="0f09b-114">`GetStackParameterSize` Wywołano na platformie z systemem innym niż x86.</span><span class="sxs-lookup"><span data-stu-id="0f09b-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="0f09b-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f09b-115">E_FAIL</span></span>|<span data-ttu-id="0f09b-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="0f09b-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="0f09b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0f09b-117">E_INVALIDARG</span></span>|<span data-ttu-id="0f09b-118">`pSize` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0f09b-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0f09b-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="0f09b-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f09b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f09b-120">Remarks</span></span>  
 <span data-ttu-id="0f09b-121">[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) metod nie ustawiaj wskaźnik stosu dla parametrów, które są przenoszone na stosie.</span><span class="sxs-lookup"><span data-stu-id="0f09b-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="0f09b-122">Zamiast tego można użyć wartości zwróconej przez `GetStackParameterSize` dostosowanie wskaźnik stosu do inicjatora unwinder macierzystego, który dostosować parametrów.</span><span class="sxs-lookup"><span data-stu-id="0f09b-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f09b-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f09b-123">Requirements</span></span>  
 <span data-ttu-id="0f09b-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f09b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f09b-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f09b-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f09b-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f09b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f09b-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f09b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f09b-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f09b-128">See Also</span></span>  
 [<span data-ttu-id="0f09b-129">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f09b-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="0f09b-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0f09b-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0f09b-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0f09b-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

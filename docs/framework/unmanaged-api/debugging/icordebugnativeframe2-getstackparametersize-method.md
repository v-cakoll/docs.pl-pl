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
ms.openlocfilehash: ca742ba9e89e1d189cfa38dead314df0d8b4e9d1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792759"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="6fb11-102">ICorDebugNativeFrame2::GetStackParameterSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="6fb11-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="6fb11-103">Zwraca skumulowany rozmiar parametrów na stosie w systemach operacyjnych x86.</span><span class="sxs-lookup"><span data-stu-id="6fb11-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fb11-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fb11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fb11-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="6fb11-106">określoną Wskaźnik do skumulowanego rozmiaru parametrów na stosie.</span><span class="sxs-lookup"><span data-stu-id="6fb11-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fb11-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="6fb11-107">Return Value</span></span>  
 <span data-ttu-id="6fb11-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="6fb11-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6fb11-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6fb11-109">HRESULT</span></span>|<span data-ttu-id="6fb11-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6fb11-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6fb11-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6fb11-111">S_OK</span></span>|<span data-ttu-id="6fb11-112">Rozmiar stosu został pomyślnie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="6fb11-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="6fb11-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6fb11-113">S_FALSE</span></span>|<span data-ttu-id="6fb11-114">`GetStackParameterSize` został wywołany na platformie innej niż x86.</span><span class="sxs-lookup"><span data-stu-id="6fb11-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="6fb11-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6fb11-115">E_FAIL</span></span>|<span data-ttu-id="6fb11-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="6fb11-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="6fb11-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6fb11-117">E_INVALIDARG</span></span>|<span data-ttu-id="6fb11-118">`pSize` jest `null`.</span><span class="sxs-lookup"><span data-stu-id="6fb11-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6fb11-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="6fb11-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fb11-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fb11-120">Remarks</span></span>  
 <span data-ttu-id="6fb11-121">Metody [ICorDebugStackWalk](icordebugstackwalk-interface.md) nie dostosowują wskaźnika stosu dla parametrów, które są wypychane na stosie.</span><span class="sxs-lookup"><span data-stu-id="6fb11-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="6fb11-122">Zamiast tego można użyć wartości zwracanej przez `GetStackParameterSize`, aby dostosować Wskaźnik stosu do inicjatora natywnego, który dostosowuje parametry.</span><span class="sxs-lookup"><span data-stu-id="6fb11-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb11-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fb11-123">Requirements</span></span>  
 <span data-ttu-id="6fb11-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fb11-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb11-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6fb11-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fb11-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6fb11-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fb11-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb11-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb11-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fb11-128">See also</span></span>

- [<span data-ttu-id="6fb11-129">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fb11-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="6fb11-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6fb11-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6fb11-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6fb11-131">Debugging</span></span>](index.md)

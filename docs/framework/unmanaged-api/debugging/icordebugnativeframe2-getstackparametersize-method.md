---
title: "ICorDebugNativeFrame2::GetStackParameterSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.GetStackParameterSize Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c265cb564718b362b1354189e59dc217b2866b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="f85c0-102">ICorDebugNativeFrame2::GetStackParameterSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="f85c0-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="f85c0-103">Zwraca całkowity rozmiar wszystkich parametrów na stosie na x86 systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="f85c0-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f85c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f85c0-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f85c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f85c0-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="f85c0-106">[out] Wskaźnik do całkowity rozmiar wszystkich parametrów na stosie.</span><span class="sxs-lookup"><span data-stu-id="f85c0-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f85c0-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f85c0-107">Return Value</span></span>  
 <span data-ttu-id="f85c0-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="f85c0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f85c0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f85c0-109">HRESULT</span></span>|<span data-ttu-id="f85c0-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f85c0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f85c0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f85c0-111">S_OK</span></span>|<span data-ttu-id="f85c0-112">Pomyślnie zwrócono rozmiar stosu.</span><span class="sxs-lookup"><span data-stu-id="f85c0-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="f85c0-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f85c0-113">S_FALSE</span></span>|<span data-ttu-id="f85c0-114">`GetStackParameterSize`Wywołano na platformie z systemem innym niż x86.</span><span class="sxs-lookup"><span data-stu-id="f85c0-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="f85c0-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f85c0-115">E_FAIL</span></span>|<span data-ttu-id="f85c0-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="f85c0-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="f85c0-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f85c0-117">E_INVALIDARG</span></span>|<span data-ttu-id="f85c0-118">`pSize`Jest `null`.</span><span class="sxs-lookup"><span data-stu-id="f85c0-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f85c0-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="f85c0-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f85c0-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f85c0-120">Remarks</span></span>  
 <span data-ttu-id="f85c0-121">[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) metod nie ustawiaj wskaźnik stosu dla parametrów, które są przenoszone na stosie.</span><span class="sxs-lookup"><span data-stu-id="f85c0-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="f85c0-122">Zamiast tego można użyć wartości zwróconej przez `GetStackParameterSize` dostosowanie wskaźnik stosu do inicjatora unwinder macierzystego, który dostosować parametrów.</span><span class="sxs-lookup"><span data-stu-id="f85c0-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f85c0-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f85c0-123">Requirements</span></span>  
 <span data-ttu-id="f85c0-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f85c0-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f85c0-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f85c0-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f85c0-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f85c0-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f85c0-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f85c0-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85c0-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f85c0-128">See Also</span></span>  
 [<span data-ttu-id="f85c0-129">ICorDebugNativeFrame2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f85c0-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="f85c0-130">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="f85c0-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f85c0-131">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f85c0-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

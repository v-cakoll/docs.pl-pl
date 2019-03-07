---
title: ICorDebugDataTarget::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0d579ffe6bf0722365e789ba3a43ce1dce06fac
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502998"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="0a8ad-102">ICorDebugDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a8ad-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="0a8ad-103">Zwraca bieżący kontekst wątku określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a8ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a8ad-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a8ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a8ad-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="0a8ad-106">[in] Identyfikator wątku, którego kontekst ma być pobrana.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="0a8ad-107">Identyfikator jest definiowany przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="0a8ad-108">[in] Bitowa kombinacja flag zależny od platformy, które wskazują, które części kontekstu powinny być odczytywane.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0a8ad-109">[in] Rozmiar `pContext`.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="0a8ad-110">[out] Bufor, w którym będzie przechowywany kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a8ad-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a8ad-111">Remarks</span></span>  
 <span data-ttu-id="0a8ad-112">Na platformach Windows `pContext` musi być `CONTEXT` struktury (zdefiniowane w pliku WinNT.h), który jest odpowiedni dla typu maszyny, określonego przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="0a8ad-113">`contextFlags` musi mieć takie same wartości jak `ContextFlags` pole `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="0a8ad-114">`CONTEXT` Struktury jest specyficznych dla procesora; odwoływać się do pliku opis pliku WinNT.h, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="0a8ad-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a8ad-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a8ad-115">Requirements</span></span>  
 <span data-ttu-id="0a8ad-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a8ad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a8ad-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a8ad-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a8ad-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a8ad-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a8ad-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a8ad-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8ad-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a8ad-120">See also</span></span>
- [<span data-ttu-id="0a8ad-121">ICorDebugDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a8ad-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="0a8ad-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0a8ad-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0a8ad-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0a8ad-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

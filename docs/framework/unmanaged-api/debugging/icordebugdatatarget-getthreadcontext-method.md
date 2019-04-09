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
ms.openlocfilehash: 2db073f6bde3ded27f8e1aa41bfcb87e764745f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174970"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="4e22f-102">ICorDebugDataTarget::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e22f-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="4e22f-103">Zwraca bieżący kontekst wątku określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="4e22f-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e22f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e22f-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e22f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e22f-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="4e22f-106">[in] Identyfikator wątku, którego kontekst ma być pobrana.</span><span class="sxs-lookup"><span data-stu-id="4e22f-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="4e22f-107">Identyfikator jest definiowany przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="4e22f-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="4e22f-108">[in] Bitowa kombinacja flag zależny od platformy, które wskazują, które części kontekstu powinny być odczytywane.</span><span class="sxs-lookup"><span data-stu-id="4e22f-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4e22f-109">[in] Rozmiar `pContext`.</span><span class="sxs-lookup"><span data-stu-id="4e22f-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="4e22f-110">[out] Bufor, w którym będzie przechowywany kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="4e22f-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e22f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e22f-111">Remarks</span></span>  
 <span data-ttu-id="4e22f-112">Na platformach Windows `pContext` musi być `CONTEXT` struktury (zdefiniowane w pliku WinNT.h), który jest odpowiedni dla typu maszyny, określonego przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4e22f-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> `contextFlags` <span data-ttu-id="4e22f-113">musi mieć takie same wartości jak `ContextFlags` pole `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="4e22f-113">must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="4e22f-114">`CONTEXT` Struktury jest specyficznych dla procesora; odwoływać się do pliku opis pliku WinNT.h, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="4e22f-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e22f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e22f-115">Requirements</span></span>  
 <span data-ttu-id="4e22f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e22f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e22f-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e22f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e22f-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e22f-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4e22f-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4e22f-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e22f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e22f-120">See also</span></span>

- [<span data-ttu-id="4e22f-121">ICorDebugDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4e22f-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="4e22f-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4e22f-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4e22f-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4e22f-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

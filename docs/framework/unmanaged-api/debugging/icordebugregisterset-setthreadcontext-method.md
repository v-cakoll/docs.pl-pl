---
title: ICorDebugRegisterSet::SetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: 8731b57206f7987efc2498a5abe62295cd1cfae5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131327"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="12ba3-102">ICorDebugRegisterSet::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="12ba3-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="12ba3-103">`SetThreadContext` nie została zaimplementowana w .NET Framework wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="12ba3-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="12ba3-104">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="12ba3-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12ba3-105">Użyj operacji wyższego poziomu [ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) , aby ustawić kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="12ba3-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ba3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="12ba3-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="12ba3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12ba3-107">Requirements</span></span>  
 <span data-ttu-id="12ba3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12ba3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ba3-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="12ba3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12ba3-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="12ba3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12ba3-111">**.NET Framework wersje:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="12ba3-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ba3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12ba3-112">See also</span></span>

- [<span data-ttu-id="12ba3-113">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="12ba3-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="12ba3-114">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="12ba3-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

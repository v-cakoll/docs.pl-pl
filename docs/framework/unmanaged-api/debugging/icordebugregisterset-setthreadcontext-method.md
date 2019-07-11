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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: debb704900d852df1d66c7bac65ab385e0d72ec5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769943"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="2af4b-102">ICorDebugRegisterSet::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="2af4b-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="2af4b-103">`SetThreadContext` nie jest zaimplementowana w .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="2af4b-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="2af4b-104">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="2af4b-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2af4b-105">Za pomocą operacji wyższego poziomu [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) można ustawić kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="2af4b-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af4b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2af4b-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2af4b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2af4b-107">Requirements</span></span>  
 <span data-ttu-id="2af4b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af4b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af4b-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2af4b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2af4b-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2af4b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2af4b-111">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="2af4b-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af4b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2af4b-112">See also</span></span>

- [<span data-ttu-id="2af4b-113">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="2af4b-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="2af4b-114">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2af4b-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

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
ms.openlocfilehash: 6ee62c903da2f2568884b9be30b22bdcdc2d2c4b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686273"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="11c93-102">ICorDebugRegisterSet::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="11c93-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="11c93-103">`SetThreadContext` nie jest zaimplementowana w .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="11c93-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="11c93-104">Nie wywołuj tej metody.</span><span class="sxs-lookup"><span data-stu-id="11c93-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11c93-105">Za pomocą operacji wyższego poziomu [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) można ustawić kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="11c93-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c93-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="11c93-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="11c93-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11c93-107">Requirements</span></span>  
 <span data-ttu-id="11c93-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11c93-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c93-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11c93-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11c93-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11c93-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11c93-111">**Wersje programu .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="11c93-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c93-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11c93-112">See also</span></span>
- [<span data-ttu-id="11c93-113">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="11c93-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="11c93-114">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="11c93-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

---
title: ICorDebugManagedCallback2::FunctionRemapComplete — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9920627ed193e9741d65fddfc54f325cb1d3758c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761047"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="eb52c-102">ICorDebugManagedCallback2::FunctionRemapComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb52c-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="eb52c-103">Powiadamia debugera, że wykonywanie kodu zostało przełączone do nowej wersji przeprowadzono edycję funkcji.</span><span class="sxs-lookup"><span data-stu-id="eb52c-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb52c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb52c-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb52c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb52c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="eb52c-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą przeprowadzono edycję funkcji.</span><span class="sxs-lookup"><span data-stu-id="eb52c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="eb52c-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek napotkano punkt przerwania ponowne mapowanie.</span><span class="sxs-lookup"><span data-stu-id="eb52c-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="eb52c-108">[in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersja funkcji aktualnie uruchomiona w wątku.</span><span class="sxs-lookup"><span data-stu-id="eb52c-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb52c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb52c-109">Remarks</span></span>  
 <span data-ttu-id="eb52c-110">To wywołanie zwrotne umożliwia debugera do odtworzenia steppery, wszelkie istniejące wcześniej.</span><span class="sxs-lookup"><span data-stu-id="eb52c-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb52c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb52c-111">Requirements</span></span>  
 <span data-ttu-id="eb52c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb52c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb52c-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb52c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb52c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb52c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb52c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb52c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb52c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb52c-116">See also</span></span>

- [<span data-ttu-id="eb52c-117">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb52c-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="eb52c-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb52c-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

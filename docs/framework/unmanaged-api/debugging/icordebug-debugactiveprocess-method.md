---
title: ICorDebug::DebugActiveProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b3869c9f96eee6f0e3066a99a58a154a2f5f2ee
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480094"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="fb9bb-102">ICorDebug::DebugActiveProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="fb9bb-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="fb9bb-103">Dołącza debuger do istniejącego procesu.</span><span class="sxs-lookup"><span data-stu-id="fb9bb-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb9bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb9bb-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb9bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb9bb-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="fb9bb-106">[in] Identyfikator procesu, do którego ma zostać dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="fb9bb-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="fb9bb-107">[in] Wartość logiczna, która jest równa `true` Jeśli debuger powinien zachowywać się jak debugera Win32 dla procesu i wysyłania niezarządzanych wywołań zwrotnych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="fb9bb-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="fb9bb-108">[out] Wskaźnik na adres obiektu "ICorDebugProcess", który reprezentuje proces, do którego został dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="fb9bb-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb9bb-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb9bb-109">Remarks</span></span>  
 <span data-ttu-id="fb9bb-110">Debugowanie międzyoperacyjne nie jest obsługiwane na platformach Win9x i innych x86, takich jak IA-64 i komputerów z procesorem AMD64 platform.</span><span class="sxs-lookup"><span data-stu-id="fb9bb-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb9bb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb9bb-111">Requirements</span></span>  
 <span data-ttu-id="fb9bb-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb9bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb9bb-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb9bb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb9bb-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb9bb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb9bb-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb9bb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb9bb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb9bb-116">See also</span></span>
- [<span data-ttu-id="fb9bb-117">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="fb9bb-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

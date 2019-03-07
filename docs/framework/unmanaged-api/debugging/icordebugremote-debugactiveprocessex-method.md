---
title: ICorDebugRemote::DebugActiveProcessEx — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eba0ff6e545a5da5d7733a157b73ddd66e717de9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477117"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="c74dc-102">ICorDebugRemote::DebugActiveProcessEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="c74dc-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="c74dc-103">Uruchamia proces na komputerze zdalnym w debugerze.</span><span class="sxs-lookup"><span data-stu-id="c74dc-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c74dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c74dc-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c74dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c74dc-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="c74dc-106">[in] Wskaźnik do [icordebugremotetarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c74dc-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="c74dc-107">Ten parametr jest używany do określenia komputera, na którym jest uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="c74dc-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="c74dc-108">[in] Identyfikator procesu, do którego ma zostać dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="c74dc-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="c74dc-109">[in] `true` Jeśli debuger powinien zachowywać się jak debugera Win32 dla procesu i wysyłania niezarządzanych wywołań zwrotnych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c74dc-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="c74dc-110">[out] Wskaźnik na adres obiektu "ICorDebugProcess", który reprezentuje proces, do którego został dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="c74dc-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c74dc-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c74dc-111">Return Value</span></span>  
 <span data-ttu-id="c74dc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c74dc-112">S_OK</span></span>  
 <span data-ttu-id="c74dc-113">Pomyślnie dołączono do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="c74dc-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="c74dc-114">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="c74dc-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c74dc-115">Nie można dołączyć do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="c74dc-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c74dc-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c74dc-116">Remarks</span></span>  
 <span data-ttu-id="c74dc-117">Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="c74dc-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c74dc-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c74dc-118">Requirements</span></span>  
 <span data-ttu-id="c74dc-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c74dc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c74dc-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c74dc-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c74dc-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c74dc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c74dc-122">**Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="c74dc-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74dc-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c74dc-123">See also</span></span>
- [<span data-ttu-id="c74dc-124">ICorDebugRemote, interfejs</span><span class="sxs-lookup"><span data-stu-id="c74dc-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="c74dc-125">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="c74dc-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="c74dc-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c74dc-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

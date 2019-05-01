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
ms.openlocfilehash: 45b919d90454c9424cadb1d4dfc3b0dfb09e5053
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782775"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="7abad-102">ICorDebugRemote::DebugActiveProcessEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="7abad-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="7abad-103">Uruchamia proces na komputerze zdalnym w debugerze.</span><span class="sxs-lookup"><span data-stu-id="7abad-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7abad-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7abad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7abad-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="7abad-106">[in] Wskaźnik do [icordebugremotetarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7abad-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="7abad-107">Ten parametr jest używany do określenia komputera, na którym jest uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="7abad-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="7abad-108">[in] Identyfikator procesu, do którego ma zostać dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="7abad-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="7abad-109">[in] `true` Jeśli debuger powinien zachowywać się jak debugera Win32 dla procesu i wysyłania niezarządzanych wywołań zwrotnych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7abad-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="7abad-110">[out] Wskaźnik na adres obiektu "ICorDebugProcess", który reprezentuje proces, do którego został dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="7abad-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7abad-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7abad-111">Return Value</span></span>  
 <span data-ttu-id="7abad-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7abad-112">S_OK</span></span>  
 <span data-ttu-id="7abad-113">Pomyślnie dołączono do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7abad-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="7abad-114">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="7abad-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7abad-115">Nie można dołączyć do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="7abad-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7abad-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7abad-116">Remarks</span></span>  
 <span data-ttu-id="7abad-117">Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="7abad-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abad-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7abad-118">Requirements</span></span>  
 <span data-ttu-id="7abad-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7abad-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abad-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7abad-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7abad-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7abad-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7abad-122">**Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="7abad-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abad-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7abad-123">See also</span></span>

- [<span data-ttu-id="7abad-124">ICorDebugRemote, interfejs</span><span class="sxs-lookup"><span data-stu-id="7abad-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="7abad-125">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="7abad-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="7abad-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7abad-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

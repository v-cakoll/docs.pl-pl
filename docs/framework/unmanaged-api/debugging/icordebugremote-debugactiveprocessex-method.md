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
ms.openlocfilehash: eb085cc486c307a308258709f4c58619597bc202
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608391"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="a9e00-102">ICorDebugRemote::DebugActiveProcessEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9e00-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="a9e00-103">Uruchamia proces na komputerze zdalnym w debugerze.</span><span class="sxs-lookup"><span data-stu-id="a9e00-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9e00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9e00-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9e00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9e00-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="a9e00-106">[in] Wskaźnik do [icordebugremotetarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a9e00-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="a9e00-107">Ten parametr jest używany do określenia komputera, na którym jest uruchomiony proces.</span><span class="sxs-lookup"><span data-stu-id="a9e00-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="a9e00-108">[in] Identyfikator procesu, do którego ma zostać dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="a9e00-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="a9e00-109">[in] `true` Jeśli debuger powinien zachowywać się jak debugera Win32 dla procesu i wysyłania niezarządzanych wywołań zwrotnych; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a9e00-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a9e00-110">[out] Wskaźnik na adres obiektu "ICorDebugProcess", który reprezentuje proces, do którego został dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="a9e00-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9e00-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a9e00-111">Return Value</span></span>  
 <span data-ttu-id="a9e00-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9e00-112">S_OK</span></span>  
 <span data-ttu-id="a9e00-113">Pomyślnie dołączono do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a9e00-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="a9e00-114">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="a9e00-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a9e00-115">Nie można dołączyć do procesu na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="a9e00-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9e00-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9e00-116">Remarks</span></span>  
 <span data-ttu-id="a9e00-117">Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a9e00-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9e00-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9e00-118">Requirements</span></span>  
 <span data-ttu-id="a9e00-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9e00-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9e00-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9e00-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9e00-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9e00-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9e00-122">**Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="a9e00-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e00-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9e00-123">See also</span></span>
- [<span data-ttu-id="a9e00-124">ICorDebugRemote, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9e00-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="a9e00-125">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9e00-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="a9e00-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a9e00-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

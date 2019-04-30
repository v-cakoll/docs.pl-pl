---
title: ICorDebug::CanLaunchOrAttach — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cf0065f1ed12ad3a37819b0a15d734a2b51ff5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697780"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="86f35-102">ICorDebug::CanLaunchOrAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="86f35-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="86f35-103">Zwraca wartość HRESULT, która wskazuje, czy uruchamianie nowego procesu lub dołączanie do określonego istniejącego procesu jest możliwe w kontekście bieżącej konfiguracji komputera i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="86f35-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86f35-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86f35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86f35-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="86f35-106">[in] Identyfikator istniejącego procesu.</span><span class="sxs-lookup"><span data-stu-id="86f35-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="86f35-107">[in] Przekaż `true` Jeśli planujesz uruchomić z włączonym debugowaniem Win32 lub dołączyć Win32 debugowania włączone; w przeciwnym razie należy przekazać `false`.</span><span class="sxs-lookup"><span data-stu-id="86f35-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86f35-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="86f35-108">Return Value</span></span>  
 <span data-ttu-id="86f35-109">S_OK, jeśli debugowanie usługi określić uruchamianie nowego procesu lub dołączanie do danego procesu jest możliwe, podane informacje o bieżącej konfiguracji komputera i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="86f35-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="86f35-110">Możliwe wartości HRESULT to:</span><span class="sxs-lookup"><span data-stu-id="86f35-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="86f35-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="86f35-111">S_OK</span></span>  
  
- <span data-ttu-id="86f35-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="86f35-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="86f35-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="86f35-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="86f35-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="86f35-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86f35-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86f35-115">Remarks</span></span>  
 <span data-ttu-id="86f35-116">Ta metoda jest wyłącznie informacyjne.</span><span class="sxs-lookup"><span data-stu-id="86f35-116">This method is purely informational.</span></span> <span data-ttu-id="86f35-117">Interfejs nie spowoduje zatrzymania można uruchomić lub dołączanie do procesu, niezależnie od wartości zwracane przez `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="86f35-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="86f35-118">Jeśli planujesz uruchomić z włączonym debugowaniem Win32 lub dołączyć z włączonym debugowaniem Win32, przekazać `true` dla `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="86f35-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="86f35-119">HRESULT zwracane przez `CanLaunchOrAttach` mogą się różnić w przypadku użycia tej opcji.</span><span class="sxs-lookup"><span data-stu-id="86f35-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f35-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86f35-120">Requirements</span></span>  
 <span data-ttu-id="86f35-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f35-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f35-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86f35-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86f35-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86f35-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86f35-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f35-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f35-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86f35-125">See also</span></span>

- [<span data-ttu-id="86f35-126">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="86f35-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

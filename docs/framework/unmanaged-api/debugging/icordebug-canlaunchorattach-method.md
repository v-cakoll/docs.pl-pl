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
ms.openlocfilehash: 805f9a5d1f2590a06bfa929c152bdfd13900531a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134279"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="668c1-102">ICorDebug::CanLaunchOrAttach — Metoda</span><span class="sxs-lookup"><span data-stu-id="668c1-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="668c1-103">Zwraca wartość HRESULT wskazującą, czy uruchomienie nowego procesu lub dołączenie do określonego istniejącego procesu jest możliwe w kontekście bieżącego komputera i konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="668c1-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="668c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="668c1-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="668c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="668c1-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="668c1-106">podczas Identyfikator istniejącego procesu.</span><span class="sxs-lookup"><span data-stu-id="668c1-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="668c1-107">podczas Przekaż `true`, jeśli planujesz uruchamianie z włączonym debugowaniem Win32 lub dołączanie z włączonym debugowaniem Win32; w przeciwnym razie Przekaż `false`.</span><span class="sxs-lookup"><span data-stu-id="668c1-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="668c1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="668c1-108">Return Value</span></span>  
 <span data-ttu-id="668c1-109">S_OK, jeśli usługa debugowania określi, że uruchomienie nowego procesu lub dołączenie do danego procesu jest możliwe, z uwzględnieniem informacji o bieżącym komputerze i konfiguracji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="668c1-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="668c1-110">Możliwe wartości HRESULT to:</span><span class="sxs-lookup"><span data-stu-id="668c1-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="668c1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="668c1-111">S_OK</span></span>  
  
- <span data-ttu-id="668c1-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="668c1-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="668c1-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="668c1-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="668c1-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="668c1-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="668c1-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="668c1-115">Remarks</span></span>  
 <span data-ttu-id="668c1-116">Ta metoda ma charakter czysty informacyjny.</span><span class="sxs-lookup"><span data-stu-id="668c1-116">This method is purely informational.</span></span> <span data-ttu-id="668c1-117">Interfejs nie zatrzymuje uruchamiania lub dołączania do procesu, niezależnie od wartości zwracanej przez `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="668c1-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="668c1-118">Jeśli planujesz uruchamianie z włączonym debugowaniem Win32 lub Dołącz z włączonym debugowaniem Win32, Przekaż `true` dla `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="668c1-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="668c1-119">Wartość HRESULT zwrócona przez `CanLaunchOrAttach` może się różnić w przypadku użycia tej opcji.</span><span class="sxs-lookup"><span data-stu-id="668c1-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="668c1-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="668c1-120">Requirements</span></span>  
 <span data-ttu-id="668c1-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="668c1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="668c1-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="668c1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="668c1-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="668c1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="668c1-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="668c1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668c1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="668c1-125">See also</span></span>

- [<span data-ttu-id="668c1-126">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="668c1-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

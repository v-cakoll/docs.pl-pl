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
ms.openlocfilehash: 3630e25b6c24edaa366f1b0fae088e760e851fa4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895405"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="40c68-102">ICorDebug::DebugActiveProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="40c68-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="40c68-103">Dołącza debuger do istniejącego procesu.</span><span class="sxs-lookup"><span data-stu-id="40c68-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40c68-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40c68-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="40c68-106">podczas Identyfikator procesu, do którego ma zostać dołączony debuger.</span><span class="sxs-lookup"><span data-stu-id="40c68-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="40c68-107">podczas Wartość logiczna, która jest ustawiona `true` na Jeśli debuger powinien zachowywać się jako debuger Win32 dla procesu i wysyłał niezarządzane wywołania zwrotne; w przeciwnym `false`razie.</span><span class="sxs-lookup"><span data-stu-id="40c68-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="40c68-108">określoną Wskaźnik do adresu obiektu "ICorDebugProcess", który reprezentuje proces, do którego został podłączony debuger.</span><span class="sxs-lookup"><span data-stu-id="40c68-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40c68-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40c68-109">Remarks</span></span>  
 <span data-ttu-id="40c68-110">Debugowanie międzyoperacyjności nie jest obsługiwane na platformach Win9x i innych niż x86, na przykład na platformach opartych na architekturze IA-64 i AMD64.</span><span class="sxs-lookup"><span data-stu-id="40c68-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c68-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40c68-111">Requirements</span></span>  
 <span data-ttu-id="40c68-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c68-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c68-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40c68-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40c68-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40c68-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40c68-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c68-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c68-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40c68-116">See also</span></span>

- [<span data-ttu-id="40c68-117">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="40c68-117">ICorDebug Interface</span></span>](icordebug-interface.md)

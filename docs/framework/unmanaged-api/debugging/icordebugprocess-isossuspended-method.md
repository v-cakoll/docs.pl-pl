---
title: ICorDebugProcess::IsOSSuspended — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039dc0d9befb038e643abc4e2524c133234f460b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492078"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="74629-102">ICorDebugProcess::IsOSSuspended — Metoda</span><span class="sxs-lookup"><span data-stu-id="74629-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="74629-103">Pobiera wartość wskazującą, czy określony wątek została zawieszona wyniku debugera zatrzymywania tego procesu.</span><span class="sxs-lookup"><span data-stu-id="74629-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74629-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74629-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74629-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74629-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="74629-106">[in] Identyfikator wątku jest zagrożona.</span><span class="sxs-lookup"><span data-stu-id="74629-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="74629-107">[out] Wskaźnik na wartość logiczną, która jest `true` , jeśli określony wątek został wstrzymany; w przeciwnym razie \*`pbSuspended` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="74629-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74629-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74629-108">Remarks</span></span>  
 <span data-ttu-id="74629-109">Podczas określonego wątku została zawieszona wyniku debugera, ten proces trwa zatrzymywanie, określony wątek Win32 zawiesić licznik jest zwiększany o jeden.</span><span class="sxs-lookup"><span data-stu-id="74629-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="74629-110">Debuger interfejsu użytkownika (UI) mogą chcieć wykonać te informacje pod uwagę wyświetlaniem systemu operacyjnego (OS) wstrzymywanie łącznej liczby wątków do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="74629-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="74629-111">`IsOSSuspended` Metoda ma sens tylko w kontekście debugowanie niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="74629-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="74629-112">Podczas debugowania zarządzanego wątki są wspólne wstrzymane, a nie zawieszony przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="74629-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74629-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74629-113">Requirements</span></span>  
 <span data-ttu-id="74629-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74629-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74629-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74629-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74629-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74629-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74629-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74629-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

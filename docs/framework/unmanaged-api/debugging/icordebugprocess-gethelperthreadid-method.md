---
title: ICorDebugProcess::GetHelperThreadID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd5e30d08e667dcd5a8be1f9502462f28290068e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494223"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="84b83-102">ICorDebugProcess::GetHelperThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="84b83-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="84b83-103">Pobiera identyfikator wątku systemu operacyjnego (OS) debugera wewnętrzny wątek pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="84b83-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84b83-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84b83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84b83-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="84b83-106">[out] Wskaźnik do systemu operacyjnego wątku identyfikator wątku wewnętrznego Pomocnik debugera.</span><span class="sxs-lookup"><span data-stu-id="84b83-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84b83-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84b83-107">Remarks</span></span>  
 <span data-ttu-id="84b83-108">Podczas debugowania zarządzanych i niezarządzanych, jest debugera ponosić odpowiedzialność za zapewnienie wątku z określonym Identyfikatorem jest uruchomiona, w przypadku trafienia punktu przerwania umieszczone przez debuger.</span><span class="sxs-lookup"><span data-stu-id="84b83-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="84b83-109">Debuger może również chcesz ukryć ten wątek od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84b83-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="84b83-110">Jeśli wątek pomocniczy, nie istnieje w procesie jeszcze `GetHelperThreadID` metoda zwraca zero w \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="84b83-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="84b83-111">Identyfikator wątku wątek pomocniczy nie może buforować, ponieważ czasem ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="84b83-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="84b83-112">Identyfikator wątku na każde zdarzenie zatrzymywanie musi ponownie zapytania.</span><span class="sxs-lookup"><span data-stu-id="84b83-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="84b83-113">Identyfikator wątku wątek pomocniczy debugera będzie prawidłowy w każdy niezarządzany [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) zdarzenia, dzięki czemu debugera określić identyfikator wątku wątku pomocnika i Ukryj go przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84b83-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="84b83-114">Wątek, który jest identyfikowany jako wątek pomocniczy podczas niezarządzanych `ICorDebugManagedCallback::CreateThread` zdarzeń nigdy nie spowoduje uruchomienia kodu zarządzanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84b83-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b83-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84b83-115">Requirements</span></span>  
 <span data-ttu-id="84b83-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84b83-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84b83-117">**Nagłówek:** CorDebug.idl.</span><span class="sxs-lookup"><span data-stu-id="84b83-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="84b83-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84b83-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="84b83-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84b83-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84b83-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84b83-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

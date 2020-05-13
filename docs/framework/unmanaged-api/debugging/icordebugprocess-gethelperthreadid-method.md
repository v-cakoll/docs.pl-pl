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
ms.openlocfilehash: fc4f4b56552c4db265d2ea123a84c7792ad53094
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213637"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="01708-102">ICorDebugProcess::GetHelperThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="01708-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="01708-103">Pobiera identyfikator wątku pomocnika wewnętrznego debugera w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="01708-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01708-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01708-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01708-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01708-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="01708-106">określoną Wskaźnik do identyfikatora wątku systemu operacyjnego wewnętrznego wątku pomocnika debugera.</span><span class="sxs-lookup"><span data-stu-id="01708-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01708-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01708-107">Remarks</span></span>  
 <span data-ttu-id="01708-108">Podczas debugowania zarządzanego i niezarządzanego, jest odpowiedzialny za debuger, aby upewnić się, że wątek o określonym IDENTYFIKATORze pozostaje uruchomiony, jeśli trafi punkt przerwania umieszczony przez debuger.</span><span class="sxs-lookup"><span data-stu-id="01708-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="01708-109">Debuger może również chcieć ukryć ten wątek od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="01708-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="01708-110">Jeśli w procesie nie istnieje jeszcze wątek pomocnika, `GetHelperThreadID` Metoda zwraca zero w \* `pThreadID` .</span><span class="sxs-lookup"><span data-stu-id="01708-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="01708-111">Nie można buforować wątku identyfikatora wątku pomocnika, ponieważ może on ulec zmianie w czasie.</span><span class="sxs-lookup"><span data-stu-id="01708-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="01708-112">W każdym zdarzeniu zatrzymywania należy wykonać ponowne zapytanie o identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="01708-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="01708-113">Identyfikator wątku wątku pomocnika debugera będzie poprawny w każdym niezarządzanym zdarzeniu [ICorDebugManagedCallback:: Isthreading](icordebugmanagedcallback-createthread-method.md) , dzięki czemu debuger może ustalić identyfikator wątku jego wątku pomocnika i ukryć go od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="01708-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="01708-114">Wątek, który jest identyfikowany jako wątek pomocnika w niezarządzanym `ICorDebugManagedCallback::CreateThread` zdarzeniu, nigdy nie będzie uruchamiał zarządzanego kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="01708-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01708-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01708-115">Requirements</span></span>  
 <span data-ttu-id="01708-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01708-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01708-117">**Nagłówek:** CorDebug. idl.</span><span class="sxs-lookup"><span data-stu-id="01708-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="01708-118">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="01708-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="01708-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="01708-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01708-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01708-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

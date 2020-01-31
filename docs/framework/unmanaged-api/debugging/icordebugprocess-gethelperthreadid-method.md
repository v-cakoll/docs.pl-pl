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
ms.openlocfilehash: d0dc301c67d09ebb15bf47cef15e642fb7c78fb9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792607"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="9e700-102">ICorDebugProcess::GetHelperThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e700-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="9e700-103">Pobiera identyfikator wątku pomocnika wewnętrznego debugera w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="9e700-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e700-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e700-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e700-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e700-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="9e700-106">określoną Wskaźnik do identyfikatora wątku systemu operacyjnego wewnętrznego wątku pomocnika debugera.</span><span class="sxs-lookup"><span data-stu-id="9e700-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e700-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e700-107">Remarks</span></span>  
 <span data-ttu-id="9e700-108">Podczas debugowania zarządzanego i niezarządzanego, jest odpowiedzialny za debuger, aby upewnić się, że wątek o określonym IDENTYFIKATORze pozostaje uruchomiony, jeśli trafi punkt przerwania umieszczony przez debuger.</span><span class="sxs-lookup"><span data-stu-id="9e700-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="9e700-109">Debuger może również chcieć ukryć ten wątek od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e700-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="9e700-110">Jeśli żaden wątek pomocnika nie istnieje jeszcze w procesie, Metoda `GetHelperThreadID` zwraca zero w \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="9e700-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="9e700-111">Nie można buforować wątku identyfikatora wątku pomocnika, ponieważ może on ulec zmianie w czasie.</span><span class="sxs-lookup"><span data-stu-id="9e700-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="9e700-112">W każdym zdarzeniu zatrzymywania należy wykonać ponowne zapytanie o identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="9e700-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="9e700-113">Identyfikator wątku wątku pomocnika debugera będzie poprawny w każdym niezarządzanym zdarzeniu [ICorDebugManagedCallback:: Isthreading](icordebugmanagedcallback-createthread-method.md) , dzięki czemu debuger może ustalić identyfikator wątku jego wątku pomocnika i ukryć go od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e700-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="9e700-114">Wątek, który jest identyfikowany jako wątek pomocnika w niezarządzanym zdarzeniu `ICorDebugManagedCallback::CreateThread` nigdy nie będzie uruchamiał zarządzanego kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e700-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e700-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e700-115">Requirements</span></span>  
 <span data-ttu-id="9e700-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e700-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e700-117">**Nagłówek:** CorDebug. idl.</span><span class="sxs-lookup"><span data-stu-id="9e700-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="9e700-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e700-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="9e700-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9e700-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e700-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e700-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

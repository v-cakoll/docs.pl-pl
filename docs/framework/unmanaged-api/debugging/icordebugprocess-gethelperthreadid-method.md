---
title: "ICorDebugProcess::GetHelperThreadID — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03e801cb58b8f5c3f658085fcee4288278e545c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="106f0-102">ICorDebugProcess::GetHelperThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="106f0-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="106f0-103">Pobiera identyfikator wątku systemu operacyjnego (OS) debugera wewnętrzny wątek pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="106f0-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="106f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="106f0-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="106f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="106f0-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="106f0-106">[out] Wskaźnik do systemu operacyjnego wątku identyfikator debugera wewnętrzny wątek pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="106f0-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="106f0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="106f0-107">Remarks</span></span>  
 <span data-ttu-id="106f0-108">Podczas debugowania zarządzane i niezarządzane, odpowiada debugera upewnij się, z określonym Identyfikatorem wątku jest uruchomiona, jeśli jego trafienia punktu przerwania, umieszczonych przez debuger.</span><span class="sxs-lookup"><span data-stu-id="106f0-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="106f0-109">Debuger może również chcesz ukryć ten wątek od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="106f0-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="106f0-110">Jeśli istnieje jeszcze w procesie nie wątek pomocniczy `GetHelperThreadID` metoda zwraca zero w \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="106f0-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="106f0-111">Identyfikator wątku wątek pomocniczy nie może buforować, ponieważ może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="106f0-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="106f0-112">Identyfikator wątku, w każdym zdarzeniu zatrzymywania musi ponownie zapytanie.</span><span class="sxs-lookup"><span data-stu-id="106f0-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="106f0-113">Identyfikator wątku wątek pomocniczy debugera jest poprawny w każdym niezarządzane [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) zdarzeń, dzięki czemu debugera do określenia Identyfikatora wątku jego wątek pomocniczy i Ukryj go przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="106f0-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="106f0-114">Wątek, który jest rozpoznawany jako wątek pomocniczy podczas niezarządzane `ICorDebugManagedCallback::CreateThread` zdarzeń nigdy nie uruchomi kod zarządzany użytkownika.</span><span class="sxs-lookup"><span data-stu-id="106f0-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="106f0-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="106f0-115">Requirements</span></span>  
 <span data-ttu-id="106f0-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="106f0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="106f0-117">**Nagłówek:** CorDebug.idl.</span><span class="sxs-lookup"><span data-stu-id="106f0-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="106f0-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="106f0-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="106f0-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="106f0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="106f0-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="106f0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

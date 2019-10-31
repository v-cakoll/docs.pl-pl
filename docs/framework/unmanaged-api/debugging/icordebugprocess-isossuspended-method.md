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
ms.openlocfilehash: 21da69d4bff0f17eb607dda45fb7dbafea8c59f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128770"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="bdfc7-102">ICorDebugProcess::IsOSSuspended — Metoda</span><span class="sxs-lookup"><span data-stu-id="bdfc7-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="bdfc7-103">Pobiera wartość wskazującą, czy określony wątek został wstrzymany w wyniku debugera zatrzymywania tego procesu.</span><span class="sxs-lookup"><span data-stu-id="bdfc7-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdfc7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdfc7-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdfc7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdfc7-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="bdfc7-106">podczas Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="bdfc7-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="bdfc7-107">określoną Wskaźnik do wartości logicznej, która jest `true`, jeśli określony wątek został zawieszony; w przeciwnym wypadku \*`pbSuspended` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="bdfc7-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdfc7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bdfc7-108">Remarks</span></span>  
 <span data-ttu-id="bdfc7-109">Gdy określony wątek zostanie zawieszony z powodu zatrzymywania tego procesu przez debuger, licznik zawieszania Win32 określonego wątku jest zwiększany o jeden.</span><span class="sxs-lookup"><span data-stu-id="bdfc7-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="bdfc7-110">Interfejs użytkownika debugera (UI) może chcieć zastosować te informacje w przypadku wyświetlenia przez użytkownika liczby wstrzymania wątku dla tego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="bdfc7-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="bdfc7-111">Metoda `IsOSSuspended` ma sens tylko w kontekście debugowania niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="bdfc7-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="bdfc7-112">Podczas debugowania zarządzanego wątki są zawieszone w trybie spółdzielni, a nie zawieszone w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="bdfc7-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdfc7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bdfc7-113">Requirements</span></span>  
 <span data-ttu-id="bdfc7-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdfc7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdfc7-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bdfc7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdfc7-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bdfc7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdfc7-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdfc7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

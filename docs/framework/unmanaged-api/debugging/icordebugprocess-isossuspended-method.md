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
ms.openlocfilehash: 9452f238bd84c9c185ca8e007acac563474d29df
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212064"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="37ecb-102">ICorDebugProcess::IsOSSuspended — Metoda</span><span class="sxs-lookup"><span data-stu-id="37ecb-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="37ecb-103">Pobiera wartość wskazującą, czy określony wątek został wstrzymany w wyniku debugera zatrzymywania tego procesu.</span><span class="sxs-lookup"><span data-stu-id="37ecb-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ecb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37ecb-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37ecb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37ecb-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="37ecb-106">podczas Identyfikator wątku.</span><span class="sxs-lookup"><span data-stu-id="37ecb-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="37ecb-107">określoną Wskaźnik do wartości logicznej, która jest w `true` przypadku zawieszenia określonego wątku; w przeciwnym razie \* `pbSuspended` jest `false` .</span><span class="sxs-lookup"><span data-stu-id="37ecb-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37ecb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37ecb-108">Remarks</span></span>  
 <span data-ttu-id="37ecb-109">Gdy określony wątek zostanie zawieszony z powodu zatrzymywania tego procesu przez debuger, licznik zawieszania Win32 określonego wątku jest zwiększany o jeden.</span><span class="sxs-lookup"><span data-stu-id="37ecb-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="37ecb-110">Interfejs użytkownika debugera (UI) może chcieć zastosować te informacje w przypadku wyświetlenia przez użytkownika liczby wstrzymania wątku dla tego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="37ecb-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="37ecb-111">`IsOSSuspended`Metoda ma sens tylko w kontekście debugowania niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="37ecb-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="37ecb-112">Podczas debugowania zarządzanego wątki są zawieszone w trybie spółdzielni, a nie zawieszone w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="37ecb-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37ecb-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37ecb-113">Requirements</span></span>  
 <span data-ttu-id="37ecb-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37ecb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ecb-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="37ecb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37ecb-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="37ecb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37ecb-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37ecb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

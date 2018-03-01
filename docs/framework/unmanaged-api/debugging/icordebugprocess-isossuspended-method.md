---
title: "ICorDebugProcess::IsOSSuspended — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 97c394e3084007227cf157c62a12df3f5cfac8e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="cc6f5-102">ICorDebugProcess::IsOSSuspended — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc6f5-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="cc6f5-103">Pobiera wartość wskazującą, czy określony wątek został wstrzymany wyniku debugera zatrzymywanie tego procesu.</span><span class="sxs-lookup"><span data-stu-id="cc6f5-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc6f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc6f5-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc6f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc6f5-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="cc6f5-106">[in] Identyfikator wątku jest zagrożona.</span><span class="sxs-lookup"><span data-stu-id="cc6f5-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="cc6f5-107">[out] Wskaźnik do wartość logiczna, która jest `true` Jeśli określony wątek został zawieszony; w przeciwnym razie \*`pbSuspended` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="cc6f5-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc6f5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc6f5-108">Remarks</span></span>  
 <span data-ttu-id="cc6f5-109">Gdy określony wątek zostało zawieszone wyniku debugera zatrzymywanie tego procesu, określony wątek Win32 zawiesić liczba jest zwiększany o jeden.</span><span class="sxs-lookup"><span data-stu-id="cc6f5-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="cc6f5-110">Debuger interfejsu użytkownika (UI) może być konieczne pobierać te informacje pod uwagę, jeśli zawiera system operacyjny (OS) zawiesić liczba wątków dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cc6f5-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="cc6f5-111">`IsOSSuspended` Metoda ma sens tylko w kontekście debugowanie niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="cc6f5-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="cc6f5-112">Podczas debugowania zarządzanego wątki są wspólnie wstrzymaną zamiast zawieszone systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="cc6f5-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6f5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc6f5-113">Requirements</span></span>  
 <span data-ttu-id="cc6f5-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc6f5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc6f5-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc6f5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc6f5-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc6f5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc6f5-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc6f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

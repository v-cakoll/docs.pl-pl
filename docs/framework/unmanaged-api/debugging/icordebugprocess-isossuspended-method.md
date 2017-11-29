---
title: "ICorDebugProcess::IsOSSuspended — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsOSSuspended
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 140855ca2828ba2a8fdf811d29fc512f6ccd20e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="32081-102">ICorDebugProcess::IsOSSuspended — Metoda</span><span class="sxs-lookup"><span data-stu-id="32081-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="32081-103">Pobiera wartość wskazującą, czy określony wątek został wstrzymany wyniku debugera zatrzymywanie tego procesu.</span><span class="sxs-lookup"><span data-stu-id="32081-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32081-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32081-104">Syntax</span></span>  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32081-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32081-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="32081-106">[in] Identyfikator wątku jest zagrożona.</span><span class="sxs-lookup"><span data-stu-id="32081-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="32081-107">[out] Wskaźnik do wartość logiczna, która jest `true` Jeśli określony wątek został zawieszony; w przeciwnym razie *`pbSuspended` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="32081-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise *`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32081-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32081-108">Remarks</span></span>  
 <span data-ttu-id="32081-109">Gdy określony wątek zostało zawieszone wyniku debugera zatrzymywanie tego procesu, określony wątek Win32 zawiesić liczba jest zwiększany o jeden.</span><span class="sxs-lookup"><span data-stu-id="32081-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="32081-110">Debuger interfejsu użytkownika (UI) może być konieczne pobierać te informacje pod uwagę, jeśli zawiera system operacyjny (OS) zawiesić liczba wątków dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="32081-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="32081-111">`IsOSSuspended` Metoda ma sens tylko w kontekście debugowanie niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="32081-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="32081-112">Podczas debugowania zarządzanego wątki są wspólnie wstrzymaną zamiast zawieszone systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="32081-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32081-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32081-113">Requirements</span></span>  
 <span data-ttu-id="32081-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32081-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32081-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32081-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32081-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32081-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32081-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32081-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

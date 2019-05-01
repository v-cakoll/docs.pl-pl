---
title: ICorDebugThread::GetUserState — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4deaa3ab4b14fbd32d45841966cfac9e33b9f31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987080"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="1d607-102">ICorDebugThread::GetUserState — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d607-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="1d607-103">Pobiera bieżący stan to ICorDebugThread użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1d607-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d607-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d607-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d607-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d607-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="1d607-106">[out] Wskaźnik do bitowa kombinacja wartości wyliczenia cordebuguserstate —, które opisują bieżący stan użytkownika tego wątku.</span><span class="sxs-lookup"><span data-stu-id="1d607-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d607-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d607-107">Remarks</span></span>  
 <span data-ttu-id="1d607-108">Stan użytkownika wątku jest stan wątku, gdy jest badany przez program, który jest debugowany.</span><span class="sxs-lookup"><span data-stu-id="1d607-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="1d607-109">Wątek może mieć wiele stanu bitów.</span><span class="sxs-lookup"><span data-stu-id="1d607-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d607-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d607-110">Requirements</span></span>  
 <span data-ttu-id="1d607-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d607-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d607-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d607-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d607-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d607-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d607-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d607-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

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
ms.openlocfilehash: 06ff8f0f13d7710d2d3d59aac4b5fdcadfe707be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418395"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="53e0f-102">ICorDebugThread::GetUserState — Metoda</span><span class="sxs-lookup"><span data-stu-id="53e0f-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="53e0f-103">Pobiera bieżący stan to ICorDebugThread użytkownika.</span><span class="sxs-lookup"><span data-stu-id="53e0f-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53e0f-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53e0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53e0f-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="53e0f-106">[out] Wskaźnik do bitowe połączenie wartości wyliczenia CorDebugUserState, które opisują bieżący stan użytkownika tego wątku.</span><span class="sxs-lookup"><span data-stu-id="53e0f-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53e0f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53e0f-107">Remarks</span></span>  
 <span data-ttu-id="53e0f-108">Stanu użytkownika w wątku jest stan wątku, gdy jest on analizowane przez program, który jest debugowany.</span><span class="sxs-lookup"><span data-stu-id="53e0f-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="53e0f-109">Wątek może mieć wiele bitów stanu.</span><span class="sxs-lookup"><span data-stu-id="53e0f-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e0f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53e0f-110">Requirements</span></span>  
 <span data-ttu-id="53e0f-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e0f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e0f-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53e0f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53e0f-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53e0f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53e0f-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e0f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

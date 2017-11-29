---
title: "ICorDebugThread3::CreateStackWalk — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.CreateStackWalk Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 022b60b50c5e38a776b9076fd4faa62a3c373b06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="dc442-102">ICorDebugThread3::CreateStackWalk — Metoda</span><span class="sxs-lookup"><span data-stu-id="dc442-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="dc442-103">Tworzy [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu stosu, którego chcesz unwind wątku.</span><span class="sxs-lookup"><span data-stu-id="dc442-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc442-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc442-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc442-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc442-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="dc442-106">[out] Wskaźnik do adresu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu stosu, którego chcesz unwind wątku.</span><span class="sxs-lookup"><span data-stu-id="dc442-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc442-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dc442-107">Return Value</span></span>  
 <span data-ttu-id="dc442-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="dc442-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dc442-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc442-109">HRESULT</span></span>|<span data-ttu-id="dc442-110">Opis</span><span class="sxs-lookup"><span data-stu-id="dc442-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc442-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc442-111">S_OK</span></span>|<span data-ttu-id="dc442-112">`ICorDebugStackWalk` Obiekt został utworzony pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dc442-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="dc442-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc442-113">E_FAIL</span></span>|<span data-ttu-id="dc442-114">`ICorDebugStackWalk` Obiekt nie został utworzony.</span><span class="sxs-lookup"><span data-stu-id="dc442-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="dc442-115">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="dc442-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc442-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc442-116">Remarks</span></span>  
 <span data-ttu-id="dc442-117">Jeśli `CreateStackWalk` metoda zakończy się powodzeniem, zwracana `ICorDebugStackWalk` ustawiono kontekstu obiektu do kontekstu bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="dc442-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc442-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc442-118">Requirements</span></span>  
 <span data-ttu-id="dc442-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc442-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc442-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc442-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc442-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc442-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc442-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc442-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc442-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc442-123">See Also</span></span>  
 [<span data-ttu-id="dc442-124">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="dc442-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dc442-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="dc442-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

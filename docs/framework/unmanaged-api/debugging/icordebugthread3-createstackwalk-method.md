---
title: ICorDebugThread3::CreateStackWalk — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fbd07638050b3861cd3cbfd45171ade5c19acb3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480653"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="44b13-102">ICorDebugThread3::CreateStackWalk — Metoda</span><span class="sxs-lookup"><span data-stu-id="44b13-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="44b13-103">Tworzy [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu wątku stosu, którego chcesz unwind.</span><span class="sxs-lookup"><span data-stu-id="44b13-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44b13-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44b13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44b13-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="44b13-106">[out] Wskaźnik do adresu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu wątku stosu, którego chcesz unwind.</span><span class="sxs-lookup"><span data-stu-id="44b13-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44b13-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="44b13-107">Return Value</span></span>  
 <span data-ttu-id="44b13-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="44b13-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44b13-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44b13-109">HRESULT</span></span>|<span data-ttu-id="44b13-110">Opis</span><span class="sxs-lookup"><span data-stu-id="44b13-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44b13-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="44b13-111">S_OK</span></span>|<span data-ttu-id="44b13-112">`ICorDebugStackWalk` Obiekt został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="44b13-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="44b13-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44b13-113">E_FAIL</span></span>|<span data-ttu-id="44b13-114">`ICorDebugStackWalk` Nie można utworzyć obiektu.</span><span class="sxs-lookup"><span data-stu-id="44b13-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="44b13-115">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="44b13-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44b13-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44b13-116">Remarks</span></span>  
 <span data-ttu-id="44b13-117">Jeśli `CreateStackWalk` metoda się powiedzie, zwrócony `ICorDebugStackWalk` ustawiono kontekstu obiektu do wątku w bieżącym kontekście.</span><span class="sxs-lookup"><span data-stu-id="44b13-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44b13-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44b13-118">Requirements</span></span>  
 <span data-ttu-id="44b13-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44b13-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44b13-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44b13-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44b13-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44b13-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44b13-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44b13-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b13-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44b13-123">See also</span></span>
- [<span data-ttu-id="44b13-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="44b13-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="44b13-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="44b13-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

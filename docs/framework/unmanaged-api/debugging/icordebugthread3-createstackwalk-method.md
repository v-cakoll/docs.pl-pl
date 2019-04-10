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
ms.openlocfilehash: 7969d8482970b13951938203262f6ce8f9bf574a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229306"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="1581a-102">ICorDebugThread3::CreateStackWalk — Metoda</span><span class="sxs-lookup"><span data-stu-id="1581a-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="1581a-103">Tworzy [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu wątku stosu, którego chcesz unwind.</span><span class="sxs-lookup"><span data-stu-id="1581a-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1581a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1581a-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1581a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1581a-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="1581a-106">[out] Wskaźnik do adresu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu wątku stosu, którego chcesz unwind.</span><span class="sxs-lookup"><span data-stu-id="1581a-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1581a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1581a-107">Return Value</span></span>  
 <span data-ttu-id="1581a-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="1581a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1581a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1581a-109">HRESULT</span></span>|<span data-ttu-id="1581a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1581a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1581a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1581a-111">S_OK</span></span>|<span data-ttu-id="1581a-112">`ICorDebugStackWalk` Obiekt został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="1581a-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="1581a-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1581a-113">E_FAIL</span></span>|<span data-ttu-id="1581a-114">`ICorDebugStackWalk` Nie można utworzyć obiektu.</span><span class="sxs-lookup"><span data-stu-id="1581a-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1581a-115">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="1581a-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1581a-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1581a-116">Remarks</span></span>  
 <span data-ttu-id="1581a-117">Jeśli `CreateStackWalk` metoda się powiedzie, zwrócony `ICorDebugStackWalk` ustawiono kontekstu obiektu do wątku w bieżącym kontekście.</span><span class="sxs-lookup"><span data-stu-id="1581a-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1581a-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1581a-118">Requirements</span></span>  
 <span data-ttu-id="1581a-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1581a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1581a-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1581a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1581a-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1581a-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1581a-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1581a-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1581a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1581a-123">See also</span></span>

- [<span data-ttu-id="1581a-124">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1581a-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1581a-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1581a-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

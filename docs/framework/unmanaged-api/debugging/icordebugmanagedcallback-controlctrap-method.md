---
title: ICorDebugManagedCallback::ControlCTrap — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e0217019aa9b8ff85716c62c27c0f4d5547074a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759791"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="465a7-102">ICorDebugManagedCallback::ControlCTrap — Metoda</span><span class="sxs-lookup"><span data-stu-id="465a7-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="465a7-103">Powiadamia debugera, CTRL + C jest zablokował w procesie, który jest debugowany.</span><span class="sxs-lookup"><span data-stu-id="465a7-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="465a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="465a7-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="465a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="465a7-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="465a7-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, w którym jest zablokował klawisze CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="465a7-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="465a7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="465a7-107">Return Value</span></span>  
  
|<span data-ttu-id="465a7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="465a7-108">HRESULT</span></span>|<span data-ttu-id="465a7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="465a7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="465a7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="465a7-110">S_OK</span></span>|<span data-ttu-id="465a7-111">Debuger będzie obsługiwać pułapki klawisze CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="465a7-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="465a7-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="465a7-112">S_FALSE</span></span>|<span data-ttu-id="465a7-113">Debuger nie będzie obsługiwać pułapki klawisze CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="465a7-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="465a7-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="465a7-114">Remarks</span></span>  
 <span data-ttu-id="465a7-115">Wszystkie domeny aplikacji w ramach procesu zostaną zatrzymane dla tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="465a7-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="465a7-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="465a7-116">Requirements</span></span>  
 <span data-ttu-id="465a7-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="465a7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="465a7-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="465a7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="465a7-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="465a7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="465a7-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="465a7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="465a7-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="465a7-121">See also</span></span>

- [<span data-ttu-id="465a7-122">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="465a7-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

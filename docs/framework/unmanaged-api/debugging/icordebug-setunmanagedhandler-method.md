---
title: ICorDebug::SetUnmanagedHandler — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: 36d314211d95dff6648753f5d550a2cfd402a918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134043"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="d18c9-102">ICorDebug::SetUnmanagedHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="d18c9-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="d18c9-103">Określa obiekt obsługi zdarzeń dla zdarzeń niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d18c9-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d18c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d18c9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d18c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d18c9-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="d18c9-106">podczas Wskaźnik do obiektu [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) , który reprezentuje procedurę obsługi zdarzeń dla niezarządzanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d18c9-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d18c9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d18c9-107">Remarks</span></span>  
 <span data-ttu-id="d18c9-108">Obiekt obsługi zdarzeń dla zdarzeń niezarządzanych musi być ustawiony po wywołaniu [ICorDebug:: Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) i przed dowolnymi wywołaniami [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) lub [ICorDebug::D ebugactiveprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="d18c9-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="d18c9-109">Jednak w przypadku starszych celów nie jest wymagane Ustawianie obiektu obsługi zdarzeń dla zdarzeń niezarządzanych do momentu zgłoszenia pierwszego natywnego zdarzenia debugowania.</span><span class="sxs-lookup"><span data-stu-id="d18c9-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="d18c9-110">Jeśli `ICorDebug::CreateProcess` ustawił flagę CREATE_SUSPENDED, natywne zdarzenia debugowania nie mogą być wysyłane do momentu wznowienia wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="d18c9-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d18c9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d18c9-111">Requirements</span></span>  
 <span data-ttu-id="d18c9-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d18c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d18c9-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d18c9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d18c9-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d18c9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d18c9-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d18c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18c9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d18c9-116">See also</span></span>

- [<span data-ttu-id="d18c9-117">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="d18c9-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

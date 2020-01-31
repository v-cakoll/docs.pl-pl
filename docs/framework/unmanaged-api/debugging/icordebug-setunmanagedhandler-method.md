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
ms.openlocfilehash: cafa1c99a8988c199d866796911d1983aabb7208
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785067"
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="1c88f-102">ICorDebug::SetUnmanagedHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c88f-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="1c88f-103">Określa obiekt obsługi zdarzeń dla zdarzeń niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="1c88f-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c88f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c88f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c88f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c88f-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="1c88f-106">podczas Wskaźnik do obiektu [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) , który reprezentuje procedurę obsługi zdarzeń dla niezarządzanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1c88f-106">[in] A pointer to an [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c88f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c88f-107">Remarks</span></span>  
 <span data-ttu-id="1c88f-108">Obiekt obsługi zdarzeń dla zdarzeń niezarządzanych musi być ustawiony po wywołaniu [ICorDebug:: Initialize](icordebug-initialize-method.md) i przed dowolnymi wywołaniami [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) lub [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="1c88f-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="1c88f-109">Jednak w przypadku starszych celów nie jest wymagane Ustawianie obiektu obsługi zdarzeń dla zdarzeń niezarządzanych do momentu zgłoszenia pierwszego natywnego zdarzenia debugowania.</span><span class="sxs-lookup"><span data-stu-id="1c88f-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="1c88f-110">Jeśli `ICorDebug::CreateProcess` ustawił flagę CREATE_SUSPENDED, natywne zdarzenia debugowania nie mogą być wysyłane do momentu wznowienia wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="1c88f-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c88f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c88f-111">Requirements</span></span>  
 <span data-ttu-id="1c88f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c88f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c88f-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c88f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c88f-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c88f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c88f-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c88f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c88f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c88f-116">See also</span></span>

- [<span data-ttu-id="1c88f-117">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c88f-117">ICorDebug Interface</span></span>](icordebug-interface.md)

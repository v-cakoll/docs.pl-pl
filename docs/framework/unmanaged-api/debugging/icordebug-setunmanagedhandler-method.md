---
title: "ICorDebug::SetUnmanagedHandler — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c1b6da9db047321583de8c3c9238ed9ad4d4ec6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="a3ac6-102">ICorDebug::SetUnmanagedHandler — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3ac6-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="a3ac6-103">Określa obiekt programu obsługi zdarzeń dla niezarządzanego zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a3ac6-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3ac6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3ac6-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3ac6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3ac6-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="a3ac6-106">[in] Wskaźnik do [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) obiekt, który reprezentuje program obsługi zdarzeń dla zdarzenia niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="a3ac6-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3ac6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3ac6-107">Remarks</span></span>  
 <span data-ttu-id="a3ac6-108">Program obsługi zdarzeń obiekt niezarządzanych zdarzenia musi być ustawiona po wywołaniu [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) i przed wszelkie wywołania [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) lub [ICorDebug::DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="a3ac6-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="a3ac6-109">Jednak do celów starszej wersji, nie należy ustawić obiektu programu obsługi zdarzeń dla zdarzenia niezarządzany do momentu pierwszego zdarzenia debugowania natywnego jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="a3ac6-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="a3ac6-110">W szczególności jeśli `ICorDebug::CreateProcess` flagę CREATE_SUSPENDED, debugowania natywnego zdarzenia nie może być przekazana do momentu wznowienia głównego wątku.</span><span class="sxs-lookup"><span data-stu-id="a3ac6-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3ac6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3ac6-111">Requirements</span></span>  
 <span data-ttu-id="a3ac6-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3ac6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3ac6-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3ac6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3ac6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3ac6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3ac6-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3ac6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3ac6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3ac6-116">See Also</span></span>  
 [<span data-ttu-id="a3ac6-117">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3ac6-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

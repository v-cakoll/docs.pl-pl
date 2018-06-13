---
title: ICorDebugManagedCallback::LogSwitch — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d5284cf6072aa5c1c11cc83355a3e9fa5c96837
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415925"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="65f5a-102">ICorDebugManagedCallback::LogSwitch — Metoda</span><span class="sxs-lookup"><span data-stu-id="65f5a-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="65f5a-103">Powiadamia debuger wspólnego języka wątku zarządzanego środowiska uruchomieniowego (języka wspólnego CLR) została wywołana metoda <xref:System.Diagnostics.Switch> klasę, aby utworzyć, zmodyfikować lub usunąć przełącznika debugowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="65f5a-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65f5a-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65f5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65f5a-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="65f5a-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające zarządzanego wątku, który utworzone, zmodyfikowane lub usunięte przełącznika debugowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="65f5a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="65f5a-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="65f5a-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="65f5a-108">[in] Wartość, która wskazuje poziom ważności opisowym komunikatem, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="65f5a-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="65f5a-109">[in] Wartość [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) wyliczenia, który wskazuje działanie wykonywane na przełączniku debugowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="65f5a-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="65f5a-110">[in] Wskaźnik do nazwy przełącznika debugowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="65f5a-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="65f5a-111">[in] Wskaźnik do nazwy elementu nadrzędnego przełącznika debugowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="65f5a-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65f5a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65f5a-112">Requirements</span></span>  
 <span data-ttu-id="65f5a-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65f5a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65f5a-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65f5a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65f5a-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65f5a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65f5a-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f5a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f5a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65f5a-117">See Also</span></span>  
 [<span data-ttu-id="65f5a-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="65f5a-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

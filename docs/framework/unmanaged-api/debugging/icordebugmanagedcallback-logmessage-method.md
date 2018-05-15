---
title: ICorDebugManagedCallback::LogMessage — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4c8494b1ffc80fc49acce01c5de0b3fd18c0f5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="96679-102">ICorDebugManagedCallback::LogMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="96679-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="96679-103">Powiadamia debuger wspólnego języka wątku zarządzanego środowiska uruchomieniowego (języka wspólnego CLR) została wywołana metoda <xref:System.Diagnostics.EventLog> klasę, aby rejestrować zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="96679-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96679-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96679-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96679-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96679-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="96679-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierające zarządzanego wątku, który rejestrowane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="96679-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="96679-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje zarządzanego wątku.</span><span class="sxs-lookup"><span data-stu-id="96679-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="96679-108">[in] Wartość [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) wyliczenia, która wskazuje poziom ważności opisowym komunikatem, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="96679-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="96679-109">[in] Wskaźnik do nazwy przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="96679-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="96679-110">[in] Wskaźnik do elementu, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="96679-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96679-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96679-111">Requirements</span></span>  
 <span data-ttu-id="96679-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96679-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96679-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96679-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96679-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96679-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96679-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96679-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96679-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96679-116">See Also</span></span>  
 [<span data-ttu-id="96679-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="96679-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

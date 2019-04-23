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
ms.openlocfilehash: cf83124af5ced7bb6458564430ceb319ce7d680a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099160"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="b3138-102">ICorDebugManagedCallback::LogMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3138-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="b3138-103">Informuje debuger, wspólnym mianownikiem zarządzanych środowiska uruchomieniowego (języka wspólnego CLR) języka została wywołana metoda <xref:System.Diagnostics.EventLog> klasy, aby rejestrować zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b3138-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3138-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3138-104">Syntax</span></span>  
  
```  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3138-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3138-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b3138-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą wątków zarządzanych, rejestrującej zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b3138-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b3138-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="b3138-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="b3138-108">[in] Wartość [logginglevelenum —](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) wyliczenie, które wskazuje poziom ważności opisowy komunikat, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3138-108">[in] A value of the [LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="b3138-109">[in] Wskaźnik na nazwę przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b3138-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="b3138-110">[in] Wskaźnik do komunikat, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b3138-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3138-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3138-111">Requirements</span></span>  
 <span data-ttu-id="b3138-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3138-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3138-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3138-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3138-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3138-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3138-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3138-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3138-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3138-116">See also</span></span>

- [<span data-ttu-id="b3138-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3138-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

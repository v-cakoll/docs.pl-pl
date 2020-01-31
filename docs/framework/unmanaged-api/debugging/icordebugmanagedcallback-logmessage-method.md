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
ms.openlocfilehash: 4306c4ae44b0ae1ade2bf374981492fa1a4df76f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788368"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="08e3c-102">ICorDebugManagedCallback::LogMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="08e3c-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="08e3c-103">Powiadamia debuger, że wątek zarządzany środowiska uruchomieniowego języka wspólnego (CLR) wezwał metodę w klasie <xref:System.Diagnostics.EventLog>, aby zarejestrować zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="08e3c-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e3c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08e3c-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08e3c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08e3c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="08e3c-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą zarządzany wątek, który zarejestrował zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="08e3c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="08e3c-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="08e3c-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="08e3c-108">podczas Wartość wyliczenia [LoggingLevelEnum —](logginglevelenum-enumeration.md) , która wskazuje poziom ważności komunikatu opisowego, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="08e3c-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="08e3c-109">podczas Wskaźnik do nazwy przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="08e3c-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="08e3c-110">podczas Wskaźnik do wiadomości, która została zapisywana w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="08e3c-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08e3c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08e3c-111">Requirements</span></span>  
 <span data-ttu-id="08e3c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08e3c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08e3c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08e3c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08e3c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="08e3c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08e3c-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08e3c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e3c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08e3c-116">See also</span></span>

- [<span data-ttu-id="08e3c-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="08e3c-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

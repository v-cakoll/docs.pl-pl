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
ms.openlocfilehash: c60af0ccfb143e68be3b987b0caf92fe3d992b4d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212714"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a><span data-ttu-id="6a091-102">ICorDebugManagedCallback::LogMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a091-102">ICorDebugManagedCallback::LogMessage Method</span></span>
<span data-ttu-id="6a091-103">Powiadamia debuger, że wątek zarządzany środowiska uruchomieniowego języka wspólnego (CLR) wezwał metodę w <xref:System.Diagnostics.EventLog> klasie, aby zarejestrować zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="6a091-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a091-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a091-104">Syntax</span></span>  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a091-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a091-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="6a091-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą zarządzany wątek, który zarejestrował zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="6a091-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that logged the event.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6a091-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="6a091-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="6a091-108">podczas Wartość wyliczenia [LoggingLevelEnum —](logginglevelenum-enumeration.md) , która wskazuje poziom ważności komunikatu opisowego, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6a091-108">[in] A value of the [LoggingLevelEnum](logginglevelenum-enumeration.md) enumeration that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="6a091-109">podczas Wskaźnik do nazwy przełącznika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6a091-109">[in] A pointer to the name of the tracing switch.</span></span>  
  
 `pMessage`  
 <span data-ttu-id="6a091-110">podczas Wskaźnik do wiadomości, która została zapisywana w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6a091-110">[in] A pointer to the message that was written to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a091-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a091-111">Requirements</span></span>  
 <span data-ttu-id="6a091-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a091-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a091-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a091-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a091-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6a091-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a091-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a091-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a091-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a091-116">See also</span></span>

- [<span data-ttu-id="6a091-117">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6a091-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

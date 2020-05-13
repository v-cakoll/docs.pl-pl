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
ms.openlocfilehash: f095bc0272e0e6f16467b9758d5e392d371139dd
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212688"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="fd261-102">ICorDebugManagedCallback::LogSwitch — Metoda</span><span class="sxs-lookup"><span data-stu-id="fd261-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="fd261-103">Powiadamia debugera, że wątek zarządzany środowiska uruchomieniowego języka wspólnego (CLR) wezwał metodę w <xref:System.Diagnostics.Switch> klasie, aby utworzyć, zmodyfikować lub usunąć przełącznik debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fd261-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd261-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd261-104">Syntax</span></span>  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd261-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd261-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="fd261-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą zarządzany wątek, który utworzył, zmodyfikował lub usunął przełącznik debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fd261-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="fd261-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="fd261-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="fd261-108">podczas Wartość wskazująca poziom ważności komunikatu opisowego, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fd261-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="fd261-109">podczas Wartość wyliczenia [LogSwitchCallReason —](logswitchcallreason-enumeration.md) , która wskazuje operację wykonywaną na przełączniku debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fd261-109">[in] A value of the [LogSwitchCallReason](logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="fd261-110">podczas Wskaźnik do nazwy przełącznika debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fd261-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="fd261-111">podczas Wskaźnik do nazwy elementu nadrzędnego przełącznika debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fd261-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd261-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd261-112">Requirements</span></span>  
 <span data-ttu-id="fd261-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd261-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd261-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fd261-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd261-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fd261-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd261-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd261-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd261-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd261-117">See also</span></span>

- [<span data-ttu-id="fd261-118">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fd261-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)

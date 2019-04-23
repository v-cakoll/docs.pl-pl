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
ms.openlocfilehash: a011485453999b9d764716356eebb2a5462f7bb9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078840"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a><span data-ttu-id="ba95c-102">ICorDebugManagedCallback::LogSwitch — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba95c-102">ICorDebugManagedCallback::LogSwitch Method</span></span>
<span data-ttu-id="ba95c-103">Informuje debuger, wspólnym mianownikiem zarządzanych środowiska uruchomieniowego (języka wspólnego CLR) języka została wywołana metoda <xref:System.Diagnostics.Switch> klasy, aby utworzyć, zmodyfikować lub usunąć przełącznik debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba95c-103">Notifies the debugger that a common language runtime (CLR) managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba95c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba95c-104">Syntax</span></span>  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba95c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba95c-105">Parameters</span></span>  
 `PAppDomain`  
 <span data-ttu-id="ba95c-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierająca zarządzane wątku, który utworzone, zmodyfikowane lub usunięte przełącznik debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba95c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread that created, modified, or deleted a debugging/tracing switch.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ba95c-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="ba95c-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="ba95c-108">[in] Wartość, która wskazuje poziom ważności opisowy komunikat, który został zapisany w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ba95c-108">[in] A value that indicates the severity level of the descriptive message that was written to the event log.</span></span>  
  
 `ulReason`  
 <span data-ttu-id="ba95c-109">[in] Wartość [logswitchcallreason —](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) wyliczenie, które wskazuje operację wykonywane na przełączniku debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba95c-109">[in] A value of the [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) enumeration that indicates the operation performed on the debugging/tracing switch.</span></span>  
  
 `pLogSwitchName`  
 <span data-ttu-id="ba95c-110">[in] Wskaźnik na nazwę przełącznika debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba95c-110">[in] A pointer to the name of the debugging/tracing switch.</span></span>  
  
 `pParentName`  
 <span data-ttu-id="ba95c-111">[in] Wskaźnik na nazwę elementu nadrzędnego przełącznik debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba95c-111">[in] A pointer to the name of the parent of the debugging/tracing switch.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba95c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba95c-112">Requirements</span></span>  
 <span data-ttu-id="ba95c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba95c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba95c-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba95c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba95c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba95c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba95c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba95c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba95c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba95c-117">See also</span></span>

- [<span data-ttu-id="ba95c-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba95c-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

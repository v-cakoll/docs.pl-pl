---
title: CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8321e5aeba435ca5f1398a9cb827a93ae821d686
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217331"
---
# <a name="clrdebuggingprocessflags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie
Zawiera wartości, które są używane przez [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|To środowisko uruchomieniowe ma zdarzenia-się w górę catch zarządzanego debugera do wysłania. Zobacz sekcję Uwagi w celu dokonania rozróżnienia między zdarzeniami zapoznać się ze zmianami i się w górę catch.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|To zdarzenie zarządzane, który jest w stanie oczekiwania <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> żądania.|  
  
## <a name="remarks"></a>Uwagi  
 Zdarzenia — wyrównywanie obejmują procesu domeny aplikacji, zestawu, modułu i powiadomienia o tworzenia wątku, które ożywiają debugera do bieżącego stanu po został on dołączony do procesu. Zdarzenia non-catch-up, które są wskazywane przez `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flagi, zawierają wszystkie inne zdarzenia debugera, takie jak wyjątki i zarządzanego debugowania (MDA) Asystenta ustawień powiadomień.  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Flagi włącza środowisko uruchomieniowe do rozróżniania wyjątek powodujący przerwanie oraz żądanie dołączenia zarządzanych debugerów, który może być anulowany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Metahost.IDL, Metahost.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

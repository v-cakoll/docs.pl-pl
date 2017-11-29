---
title: "CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_PROCESS_FLAGS
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords: CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5040b1e1eb7ec4bd814329de156fcdfeb9c383c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="clrdebuggingprocessflags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS — Wyliczenie
Udostępnia wartości, które są używane przez [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.  
  
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
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|To środowisko wykonawcze ma zdarzeń debugera zarządzanych z systemem innym niż up catch do wysłania. W sekcji uwag różnicy między zdarzeniami wyrównującej i pracy z systemem innym niż catch.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|Zarządzane zdarzenia, które jest w stanie oczekiwania jest <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> żądania.|  
  
## <a name="remarks"></a>Uwagi  
 Przechwycenie zdarzeń to proces, domeny aplikacji zestawu, modułu i powiadomień Tworzenie wątków, które dostosowania debugera do bieżącego stanu po został dołączony do procesu. Non-catch-up zdarzenia, które są oznaczone `CLR_DEBUGGING_MANAGED_EVENT_PENDING` Flaga, obejmują wszystkie inne zdarzenia debugera, takie jak wyjątków i zarządzanego debugowania (MDA) Asystenta powiadomienia.  
  
 `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Flaga umożliwia środowiska uruchomieniowego w celu rozróżnienia wyjątek powodujący przerwanie i żądanie, aby dołączyć debuger zarządzany, które mogą zostać anulowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Metahost.idl, Metahost.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie — wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

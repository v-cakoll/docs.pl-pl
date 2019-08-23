---
title: ICorDebugHeapValue, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb130f11975eb95db7807126d6f163425439b0c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914898"
---
# <a name="icordebugheapvalue-interface"></a>ICorDebugHeapValue, interfejs

Podklasa elementu "ICorDebugValue" reprezentująca obiekt, który został zebrany przez moduł zbierający elementy bezużyteczne środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateRelocBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|Nie zaimplementowane.|  
|[IsValid, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten `ICorDebugHeapValue` element jest prawidłowy lub został odrzucony przez moduł zbierający elementy bezużyteczne. Ta metoda jest przestarzała w .NET Framework w wersji 2,0.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugFunction2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: da440b7d2da57511545d3b63700662eb544660fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137779"
---
# <a name="icordebugfunction2-interface"></a>ICorDebugFunction2 — Interfejs

Logicznie rozszerza interfejs ICorDebugFunction w celu zapewnienia Tylko mój kod obsługi debugowania krok po kroku, który pomija kod niebędący użytkownikiem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateNativeCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|(Jeszcze nie zaimplementowano). Pobiera wskaźnik interfejsu do ICorDebugCodeEnum, który zawiera instrukcje kodu natywnego w funkcji, do której odwołuje się ten obiekt ICorDebugFunction2.|  
|[GetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|Pobiera wartość wskazującą, czy ta funkcja jest oznaczona jako kod użytkownika.|  
|[GetVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|Pobiera wersję Edytuj i Kontynuuj tej funkcji.|  
|[SetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|Oznacza tę funkcję do Tylko mój kod taktowania.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

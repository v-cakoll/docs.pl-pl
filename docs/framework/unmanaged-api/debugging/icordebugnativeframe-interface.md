---
title: ICorDebugNativeFrame — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbdb17bcd502b75da0a73d9a36cf36d6564320bc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975488"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame — Interfejs

Wyspecjalizowana implementacja ICorDebugFrame wykorzystywana do ramek natywnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Pobiera wartość wskazującą, czy jest bezpiecznie Ustaw wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie natywnym.|  
|[GetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Pobiera przesunięcie ramki stosu w kodzie natywnym.|  
|[GetLocalDoubleRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Pobiera wskaźnik do ICorDebugValue, która reprezentuje wartość argumentu lub zmiennej lokalnej, przechowywane w dwóch rejestrów pamięci ramka natywna.|  
|[GetLocalMemoryRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość zmiennej lokalnej, z których niski bity są przechowywane w określonej rejestru i starsze bity są przechowywane na adres pamięci określonej.|  
|[GetLocalMemoryValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość przechowywaną w adres pamięci określonej zmiennej lokalnej.|  
|[GetLocalRegisterMemoryValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość zmiennej lokalnej, którego starsze bity są przechowywane w określonej rejestru i niski bity są przechowywane pod adresem określonym pamięci|  
|[GetLocalRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość argumentu lub zmiennej lokalnej, przechowywane w określonej rejestru macierzystego.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Pobiera wskaźnik do [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) reprezentujący rejestru, określić dla niej `ICorDebugNativeFrame`.|  
|[SetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie natywnym.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

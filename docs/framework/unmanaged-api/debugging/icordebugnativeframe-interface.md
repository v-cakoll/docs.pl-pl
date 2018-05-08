---
title: ICorDebugNativeFrame Interface1
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
ms.openlocfilehash: 7996d5800e99d8e6161e24f34604aff3e4e906bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugnativeframe-interface1"></a>ICorDebugNativeFrame Interface1
Specjalne implementacja ICorDebugFrame używany dla ramek natywnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Pobiera wartość wskazującą, czy jest to bezpieczne ustawienia wskaźnika instrukcji w określonej lokalizacji przesunięcia w kodzie natywnym.|  
|[GetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Pobiera przesunięcie ramki stosu w kodzie natywnym.|  
|[GetLocalDoubleRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Pobiera wskaźnik do ICorDebugValue reprezentujący wartość argumentu lub zmienna lokalna przechowywane w dwóch rejestrów pamięci ramka natywna.|  
|[GetLocalMemoryRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Pobiera wskaźnik do `ICorDebugValue` reprezentujący wartość zmiennej lokalnej, którego niski bity są przechowywane w rejestrze określonego i bitów znajdują się pod adresem określonym pamięci.|  
|[GetLocalMemoryValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Pobiera wskaźnik do `ICorDebugValue` reprezentujący wartość zmiennej lokalnej przechowywane pod adresem określonym pamięci.|  
|[GetLocalRegisterMemoryValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Pobiera wskaźnik do `ICorDebugValue` reprezentujący wartość zmiennej lokalnej, którego bitów są przechowywane w rejestrze określonego i niski bity są przechowywane pod adresem określonym pamięci|  
|[GetLocalRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Pobiera wskaźnik do `ICorDebugValue` reprezentujący wartość argumentu lub przechowywane w rejestrze natywnego określonej zmiennej lokalnej.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Pobiera wskaźnik do [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) reprezentujący rejestru ustawić dla tego `ICorDebugNativeFrame`.|  
|[SetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Ustawia wskaźnik instrukcji w określonej lokalizacji przesunięcia w kodzie natywnym.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

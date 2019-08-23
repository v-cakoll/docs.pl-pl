---
title: ICorDebugNativeFrame, interfejs
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
ms.openlocfilehash: c01346b42fff812f8358482ae0e8570c03ee9231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912802"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame, interfejs

Wyspecjalizowana implementacja ICorDebugFrame używana w przypadku ramek natywnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Pobiera wartość wskazującą, czy można bezpiecznie ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.|  
|[GetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Pobiera przesunięcie ramki stosu do kodu natywnego.|  
|[GetLocalDoubleRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Pobiera wskaźnik do elementu ICorDebugValue, który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w dwóch rejestrach pamięci ramki natywnej.|  
|[GetLocalMemoryRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Pobiera wskaźnik do obiektu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej, w której niskie bity są przechowywane w określonym rejestrze, a duże bity są przechowywane w określonym adresie pamięci.|  
|[GetLocalMemoryValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Pobiera wskaźnik do elementu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej przechowywanej w określonym adresie pamięci.|  
|[GetLocalRegisterMemoryValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Pobiera wskaźnik do obiektu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej, w której duże bity są przechowywane w określonym rejestrze, a niskie bity są przechowywane w określonym adresie pamięci|  
|[GetLocalRegisterValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Pobiera wskaźnik do elementu `ICorDebugValue` , który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w określonym rejestrze macierzystym.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Pobiera wskaźnik do elementu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , który reprezentuje zestaw rejestru dla tego `ICorDebugNativeFrame`elementu.|  
|[SetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.|  
  
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

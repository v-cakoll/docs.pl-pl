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
ms.openlocfilehash: 41ac0b29ade2f78b893df72e8a17624373f6dd78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792794"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame, interfejs

Wyspecjalizowana implementacja ICorDebugFrame używana w przypadku ramek natywnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetIP, metoda](icordebugnativeframe-cansetip-method.md)|Pobiera wartość wskazującą, czy można bezpiecznie ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.|  
|[GetIP, metoda](icordebugnativeframe-getip-method.md)|Pobiera przesunięcie ramki stosu do kodu natywnego.|  
|[GetLocalDoubleRegisterValue, metoda](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Pobiera wskaźnik do elementu ICorDebugValue, który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w dwóch rejestrach pamięci ramki natywnej.|  
|[GetLocalMemoryRegisterValue, metoda](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Pobiera wskaźnik do `ICorDebugValue`, który reprezentuje wartość zmiennej lokalnej, w której niskie bity są przechowywane w określonym rejestrze, a duże bity są przechowywane przy określonym adresie pamięci.|  
|[GetLocalMemoryValue, metoda](icordebugnativeframe-getlocalmemoryvalue-method.md)|Pobiera wskaźnik do `ICorDebugValue`, który reprezentuje wartość zmiennej lokalnej przechowywanej w określonym adresie pamięci.|  
|[GetLocalRegisterMemoryValue, metoda](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Pobiera wskaźnik do `ICorDebugValue`, który reprezentuje wartość zmiennej lokalnej, w której duże bity są przechowywane w określonym rejestrze, a niskie bity są przechowywane w określonym adresie pamięci|  
|[GetLocalRegisterValue, metoda](icordebugnativeframe-getlocalregistervalue-method.md)|Pobiera wskaźnik do `ICorDebugValue`, który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w określonym rejestrze macierzystym.|  
|[GetRegisterSet, metoda](icordebugnativeframe-getregisterset-method.md)|Pobiera wskaźnik do elementu [ICorDebugRegisterSet](icordebugregisterset-interface.md) , który reprezentuje zestaw rejestru dla tego `ICorDebugNativeFrame`.|  
|[SetIP, metoda](icordebugnativeframe-setip-method.md)|Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)

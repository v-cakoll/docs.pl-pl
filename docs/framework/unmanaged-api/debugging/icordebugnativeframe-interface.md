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
ms.openlocfilehash: dd87745a29514a2f9f05aa142baae4e05d4b4a7b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206600"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame, interfejs

Wyspecjalizowana implementacja ICorDebugFrame używana w przypadku ramek natywnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetIP, metoda](icordebugnativeframe-cansetip-method.md)|Pobiera wartość wskazującą, czy można bezpiecznie ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.|  
|[GetIP, metoda](icordebugnativeframe-getip-method.md)|Pobiera przesunięcie ramki stosu do kodu natywnego.|  
|[GetLocalDoubleRegisterValue, metoda](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Pobiera wskaźnik do elementu ICorDebugValue, który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w dwóch rejestrach pamięci ramki natywnej.|  
|[GetLocalMemoryRegisterValue, metoda](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Pobiera wskaźnik do obiektu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej, w której niskie bity są przechowywane w określonym rejestrze, a duże bity są przechowywane w określonym adresie pamięci.|  
|[GetLocalMemoryValue, metoda](icordebugnativeframe-getlocalmemoryvalue-method.md)|Pobiera wskaźnik do elementu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej przechowywanej w określonym adresie pamięci.|  
|[GetLocalRegisterMemoryValue, metoda](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Pobiera wskaźnik do obiektu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej, w której duże bity są przechowywane w określonym rejestrze, a niskie bity są przechowywane w określonym adresie pamięci|  
|[GetLocalRegisterValue, metoda](icordebugnativeframe-getlocalregistervalue-method.md)|Pobiera wskaźnik do elementu `ICorDebugValue` , który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w określonym rejestrze macierzystym.|  
|[GetRegisterSet — Metoda](icordebugnativeframe-getregisterset-method.md)|Pobiera wskaźnik do elementu [ICorDebugRegisterSet](icordebugregisterset-interface.md) , który reprezentuje zestaw rejestru dla tego elementu `ICorDebugNativeFrame` .|  
|[SetIP — Metoda](icordebugnativeframe-setip-method.md)|Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)

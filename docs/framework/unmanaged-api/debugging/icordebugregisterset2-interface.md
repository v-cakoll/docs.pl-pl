---
title: ICorDebugRegisterSet2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: 161358fab9a4601e7b718321273d493bd84a3228
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792008"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 — Interfejs
Rozszerza możliwości interfejsu [ICorDebugRegisterSet](icordebugregisterset-interface.md) dla platform sprzętowych, które mają więcej niż 64 rejestrów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRegisters, metoda](icordebugregisterset2-getregisters-method.md)|Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.|  
|[GetRegistersAvailable, metoda](icordebugregisterset2-getregistersavailable-method.md)|Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrów.|  
|[SetRegisters, metoda](icordebugregisterset2-setregisters-method.md)|Nie zaimplementowane w .NET Framework w wersji 2,0.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [ICorDebugRegisterSet, interfejs](icordebugregisterset-interface.md)

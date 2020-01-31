---
title: ICorDebugRegisterSet — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: f435db28d5c85d576f69e7612841fc46ae142332
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792070"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet — Interfejs
Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRegisters, metoda](icordebugregisterset-getregisters-method.md)|Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.|  
|[GetRegistersAvailable, metoda](icordebugregisterset-getregistersavailable-method.md)|Pobiera maskę bitową wskazującą, które rejestry w tym `ICorDebugRegisterSet` są obecnie dostępne.|  
|[GetThreadContext, metoda](icordebugregisterset-getthreadcontext-method.md)|Pobiera kontekst bieżącego wątku.|  
|[SetRegisters, metoda](icordebugregisterset-setregisters-method.md)|Nie zaimplementowane dla .NET Framework w wersji 2,0.|  
|[SetThreadContext, metoda](icordebugregisterset-setthreadcontext-method.md)|Nie zaimplementowane dla .NET Framework 2,0.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugRegisterSet` obsługuje tylko rejestry 32-bitowe. Użyj interfejsu [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) na platformach, takich jak IA-64, które wymagają dodatkowych rejestrów.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [ICorDebugRegisterSet2, interfejs](icordebugregisterset2-interface.md)

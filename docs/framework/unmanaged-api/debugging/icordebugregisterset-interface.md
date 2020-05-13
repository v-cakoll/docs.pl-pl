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
ms.openlocfilehash: 7c60fa775b82372b50d1eb3891f107b97df3e73a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378270"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet — Interfejs
Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRegisters — Metoda](icordebugregisterset-getregisters-method.md)|Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.|  
|[GetRegistersAvailable — Metoda](icordebugregisterset-getregistersavailable-method.md)|Pobiera maskę bitową wskazującą, które rejestry w tej `ICorDebugRegisterSet` chwili są dostępne.|  
|[GetThreadContext — Metoda](icordebugregisterset-getthreadcontext-method.md)|Pobiera kontekst bieżącego wątku.|  
|[SetRegisters, metoda](icordebugregisterset-setregisters-method.md)|Nie zaimplementowane dla .NET Framework w wersji 2,0.|  
|[SetThreadContext, metoda](icordebugregisterset-setthreadcontext-method.md)|Nie zaimplementowane dla .NET Framework 2,0.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugRegisterSet`Interfejs obsługuje tylko rejestry 32-bitowe. Użyj interfejsu [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) na platformach, takich jak IA-64, które wymagają dodatkowych rejestrów.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [ICorDebugRegisterSet2 — Interfejs](icordebugregisterset2-interface.md)

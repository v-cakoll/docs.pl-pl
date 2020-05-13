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
ms.openlocfilehash: f989f1c1f29c63af54ff125f4ad1aaa2bcee6757
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378197"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 — Interfejs
Rozszerza możliwości interfejsu [ICorDebugRegisterSet](icordebugregisterset-interface.md) dla platform sprzętowych, które mają więcej niż 64 rejestrów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRegisters — Metoda](icordebugregisterset2-getregisters-method.md)|Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.|  
|[GetRegistersAvailable — Metoda](icordebugregisterset2-getregistersavailable-method.md)|Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrów.|  
|[SetRegisters, metoda](icordebugregisterset2-setregisters-method.md)|Nie zaimplementowane w .NET Framework w wersji 2,0.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [ICorDebugRegisterSet — Interfejs](icordebugregisterset-interface.md)

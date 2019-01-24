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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30cecaa1832ba9d45782b164ee65a2f39f28a8f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605409"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 — Interfejs
Rozszerza możliwości [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interfejsu dla platform sprzętowych, które mają więcej niż 64 rejestrów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRegisters, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod) określonej przez Maska bitów.|  
|[GetRegistersAvailable, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrach.|  
|[SetRegisters, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|Nie jest zaimplementowana w .NET Framework w wersji 2.0.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

---
title: ICorDebugRegisterSet::GetRegistersAvailable — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3174be7237bcdbd5a12f38f04d6e67d9eb9a573e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421856"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>ICorDebugRegisterSet::GetRegistersAvailable — Metoda
Pobiera bit maski wskazujący, który rejestruje w tym [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) są obecnie dostępne.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAvailable`  
 [out] Maska bitowa, która wskazuje, który rejestruje są obecnie dostępne.  
  
## <a name="remarks"></a>Uwagi  
 Rejestr może być niedostępna, jeśli nie można określić wartość dla danej sytuacji.  
  
 Zwrócony maska zawiera nieco dla poszczególnych rejestru (1 << indeks rejestru). Wartość bitowa wynosi 1, jeśli rejestr jest dostępny, lub wartość 0, jeśli nie jest dostępna.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

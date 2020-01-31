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
ms.openlocfilehash: b137b956e06a2b2954918e4024860f9b234e7583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792107"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>ICorDebugRegisterSet::GetRegistersAvailable — Metoda
Pobiera maskę bitową wskazującą, które rejestry w tym [ICorDebugRegisterSet](icordebugregisterset-interface.md) są obecnie dostępne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAvailable`  
 określoną Maska bitów wskazująca, które rejestry są obecnie dostępne.  
  
## <a name="remarks"></a>Uwagi  
 Rejestr może być niedostępny, jeśli nie można ustalić jego wartości dla danej sytuacji.  
  
 Zwracana Maska zawiera bit dla każdej rejestracji (1 < < indeks rejestru). Wartość bitowa to 1, jeśli rejestr jest dostępny, lub 0, jeśli nie jest dostępny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet, interfejs](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interfejs](icordebugregisterset2-interface.md)

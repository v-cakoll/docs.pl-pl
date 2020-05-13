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
ms.openlocfilehash: 74eef0c1ec456d647e5a58e5009d2c77e5002289
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378292"
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
  
 Zwracana Maska zawiera bit dla każdej rejestracji (1 << indeksem rejestru). Wartość bitowa to 1, jeśli rejestr jest dostępny, lub 0, jeśli nie jest dostępny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugRegisterSet — Interfejs](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 — Interfejs](icordebugregisterset2-interface.md)

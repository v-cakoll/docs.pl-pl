---
title: ICorDebugRegisterSet2::GetRegistersAvailable — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: 00c9939b25f395010f6ea5832b405c3e9928a223
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792027"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable — Metoda
Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `numChunks`  
 podczas Rozmiar tablicy `availableRegChunks`.  
  
 `availableRegChunks`  
 określoną Tablica bajtów, z których każdy bit odnosi się do rejestru. Jeśli rejestr jest dostępny, zostanie ustawiony odpowiedni bit rejestru.  
  
## <a name="remarks"></a>Uwagi  
 Wartości wyliczenia CorDebugRegister — określają rejestry różnych mikroprocesorów. Górne pięć bitów każdej wartości jest indeksem do `availableRegChunks` tablicy bajtów. Mniejsze trzy bity każdej wartości określają pozycję bitową w ramach indeksowanego bajtu. Uwzględniając `CorDebugRegister` wartość określającą konkretny rejestr, pozycja rejestru w masce jest określana w następujący sposób:  
  
1. Wyodrębnij indeks wymagany do uzyskania dostępu do poprawnego bajtu w tablicy `availableRegChunks`:  
  
     `CorDebugRegister` wartość > > 3  
  
2. Wyodrębnij pozycję bitową w zaindeksowanym bajcie, gdzie bit zero jest najmniej znaczącym bitem:  
  
     `CorDebugRegister` wartość & 7  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet2, interfejs](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet, interfejs](icordebugregisterset-interface.md)

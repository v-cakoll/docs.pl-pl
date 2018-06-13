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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3a9cdb49c1a44dbc68cd4b7ccf4d4781ce5c539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421895"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable — Metoda
Pobiera tablicę bajtów zawiera mapę bitową rejestry dostępne.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `numChunks`  
 [in] Rozmiar `availableRegChunks` tablicy.  
  
 `availableRegChunks`  
 [out] Tablica bajtów, każdy bit odpowiada rejestru. Jeśli rejestr jest dostępny, odpowiadający mu bit rejestru jest ustawiona.  
  
## <a name="remarks"></a>Uwagi  
 Wartości właściwości cordebugregister — wyliczenie określają rejestry mikroprocesorami inny. Górny pięć bitów każdej wartości są indeks `availableRegChunks` tablicę bajtów. Niższe trzy usługi bits każdej wartości zidentyfikować Pozycja bitu w indeksowanych bajtów. Podane `CorDebugRegister` wartość, która określa rejestr określonej pozycji rejestru maski jest określane w następujący sposób:  
  
1.  Wyodrębnij indeksu musiał uzyskać dostęp prawidłowe bajty w `availableRegChunks` tablicy:  
  
     `CorDebugRegister` wartość >> 3  
  
2.  Wyodrębnij Pozycja bitu w indeksowanych byte, gdzie bit zero jest bitem:  
  
     `CorDebugRegister` Wartość & 7  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

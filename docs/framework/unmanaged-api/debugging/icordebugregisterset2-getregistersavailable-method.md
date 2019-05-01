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
ms.openlocfilehash: 1522d643a69c47eec03770a8f51756dd4250075a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782827"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>ICorDebugRegisterSet2::GetRegistersAvailable — Metoda
Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrach.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `numChunks`  
 [in] Rozmiar `availableRegChunks` tablicy.  
  
 `availableRegChunks`  
 [out] Tablica bajtów, każdy bit odnosi się do rejestru. Jeśli rejestr jest dostępny, odpowiadający mu bit rejestru jest ustawiona.  
  
## <a name="remarks"></a>Uwagi  
 Wartości wyliczenia cordebugregister — Określ rejestrów mikroprocesory różne. Górny pięć bitów każdej wartości są Indeksuj do `availableRegChunks` tablicę bajtów. Niższe trzy usługi bits w każdej wartości identyfikują Pozycja bitu w indeksowanych bajtów. Biorąc pod uwagę `CorDebugRegister` wartość, która określa określonego rejestru, pozycji Zarejestruj maski jest określany w następujący sposób:  
  
1. Wyodrębnij indeksu umożliwiającymi dostęp poprawne bajtów w `availableRegChunks` tablicy:  
  
     `CorDebugRegister` wartość >> 3  
  
2. Wyodrębnij Pozycja bitu w indeksowanych bajtów, gdzie bit zero jest najmniej znaczący bit:  
  
     `CorDebugRegister` Wartość & 7  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

---
title: "ICorDebugRegisterSet2::GetRegistersAvailable — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f91b30b2ab50fc74049365d5c290bbaae1e20b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
     `CorDebugRegister`wartość >> 3  
  
2.  Wyodrębnij Pozycja bitu w indeksowanych byte, gdzie bit zero jest bitem:  
  
     `CorDebugRegister`Wartość & 7  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRegisterSet2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

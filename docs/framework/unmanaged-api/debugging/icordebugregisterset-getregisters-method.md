---
title: "ICorDebugRegisterSet::GetRegisters — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7edae3d3be1bcfb80b7a1e432fd5f25e119f078f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters — Metoda
Pobiera wartość każdego rejestru (na komputerze, który jest aktualnie wykonywany kodu) określonym przez maska bitowa.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mask`  
 [in] Maska bitowa, która określa rejestru, które mają być pobierane wartości. Każdy bit odpowiada rejestru. Jeśli bit ma wartość 1, wartość rejestru jest pobierana; w przeciwnym razie wartość rejestru nie została pobrana.  
  
 `regCount`  
 [in] Liczba wartości rejestru, które mają zostać pobrane.  
  
 `regBuffer`  
 [out] Tablica `CORDB_REGISTER` obiektów, z których każdy odbiera wartość rejestru.  
  
## <a name="remarks"></a>Uwagi  
 Rozmiar tablicy powinna być równa Liczba bitów w maska bitowa. `regCount` Parametr określa liczbę elementów w buforze, który będzie otrzymywał wartości rejestru. Jeśli `regCount` wartość jest za mały dla liczby rejestrów wskazywanym przez maski, wyższy rejestrów numerowane zostanie obcięty z zestawu. Jeśli `regCount` wartość jest zbyt duża, nieużywane `regBuffer` elementy zostaną zmodyfikowane.  
  
 Jeśli maska bitowa określa rejestru, który jest niedostępny, `GetRegisters` zwraca nieokreśloną wartość rejestru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRegisterSet — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [ICorDebugRegisterSet2 — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)

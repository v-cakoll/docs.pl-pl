---
title: ICorDebugComObjectValue::GetCachedInterfacePointers — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da0e62250dbef9be93ccee7020e23c3f83e85592
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223280"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers — Metoda
Pobiera wskaźniki interfejsu raw, buforowane na bieżącym wywoływana otoka środowiska uruchomieniowego (RCW).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIInspectableOnly`  
 [in] Wartość, która wskazuje, czy metoda zwróci tylko [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfejsów (`IInspectable` interfejsów) lub wszystkie interfejsy COM, które są buforowane przez otoka wywoływana w czasie wykonywania (RCW).  
  
 `celt`  
 [in] Liczba obiektów, których adresy, które mają być pobierane.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby `CORDB_ADDRESS` wartości zwracanych w rzeczywistości w `ptrs`.  
  
 `ptrs`  
 Wskaźnik do tablicy adres początkowy `CORDB_ADDRESS` wartości, które zawierają adresy pamięci podręcznej obiektów interfejsu.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugComObjectValue — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

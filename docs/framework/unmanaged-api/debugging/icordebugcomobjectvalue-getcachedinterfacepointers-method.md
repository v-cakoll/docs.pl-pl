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
ms.openlocfilehash: 9d1d6d2f506086dd3204053b0b635da2e7cdc87e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783953"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers — Metoda
Pobiera pierwotne wskaźniki interfejsu w pamięci podręcznej dla bieżącej otoki (RCW) w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIInspectableOnly`  
 podczas Wartość wskazująca, czy metoda zwróci tylko środowisko wykonawcze systemu Windows interfejsy (`IInspectable` Interfaces) czy wszystkie interfejsy COM, które są buforowane przez otokę wywoływaną przez środowisko uruchomieniowe (OTOKa).  
  
 `celt`  
 podczas Liczba obiektów, których adresy mają zostać pobrane.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby wartości `CORDB_ADDRESS` faktycznie zwróconych w `ptrs`.  
  
 `ptrs`  
 Wskaźnik do adresu początkowego tablicy wartości `CORDB_ADDRESS`, które zawierają adresy buforowanych obiektów interfejsu.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugComObjectValue, interfejs](icordebugcomobjectvalue-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)

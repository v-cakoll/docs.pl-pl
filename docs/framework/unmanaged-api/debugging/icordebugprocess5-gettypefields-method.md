---
title: ICorDebugProcess5::GetTypeFields — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178589"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields — Metoda
Zawiera informacje o polach należących do typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [w] Identyfikator typu, którego informacje o polu są pobierane.  
  
 `celt`  
 [w] Liczba [obiektów COR_FIELD,](cor-field-structure.md) których informacje o polu mają zostać pobrane.  
  
 `fields`  
 [na zewnątrz] Tablica [COR_FIELD](cor-field-structure.md) obiektów, które zawierają informacje o polach należących do typu.  
  
 `pceltNeeded`  
 [na zewnątrz] Wskaźnik do liczby [obiektów COR_FIELD](cor-field-structure.md) uwzględnionych w `fields`pliku .  
  
## <a name="remarks"></a>Uwagi  
 Parametr, `celt` który określa liczbę pól, których informacje o polu użyto metody do zapełnienia, `fields`powinien odpowiadać wartości `COR_TYPE_LAYOUT::numFields` pola.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess5, interfejs](icordebugprocess5-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)

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
ms.openlocfilehash: 644b5ed751caaf1809250244b37badc8037b0f57
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792352"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields — Metoda
Zawiera informacje o polach, które należą do typu.  
  
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
 podczas Identyfikator typu, którego informacje o polu są pobierane.  
  
 `celt`  
 podczas Liczba obiektów [COR_FIELD](cor-field-structure.md) , których informacje o polach mają być pobierane.  
  
 `fields`  
 określoną Tablica obiektów [COR_FIELD](cor-field-structure.md) , które zawierają informacje o polach, które należą do typu.  
  
 `pceltNeeded`  
 określoną Wskaźnik do liczby [COR_FIELD](cor-field-structure.md) obiektów zawartych w `fields`.  
  
## <a name="remarks"></a>Uwagi  
 `celt` parametr, który określa liczbę pól, których informacje pola są używane przez metodę do wypełniania `fields`, powinien odpowiadać wartości pola `COR_TYPE_LAYOUT::numFields`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess5, interfejs](icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)

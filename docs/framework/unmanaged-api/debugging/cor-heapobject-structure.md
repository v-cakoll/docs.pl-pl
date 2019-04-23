---
title: COR_HEAPOBJECT — Struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f179b58ff8eb51e2843780d3212cf38ed7d13216
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168834"
---
# <a name="corheapobject-structure"></a>COR_HEAPOBJECT — Struktura
Zawiera informacje dotyczące obiektu na stosie zarządzanym.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`address`|Adres obiektu w pamięci.|  
|`size`|Całkowity rozmiar obiektu w bajtach.|  
|`type`|A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, który reprezentuje typ obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_HEAPOBJECT` wystąpienia mogą być pobierane według wyliczania [icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu, który jest wypełniana przez wywołanie metody [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.  
  
 A `COR_HEAPOBJECT` wystąpienie zawiera informacje o obiekt na żywo w zarządzanym stosie albo o obiekt, który nie jest ścieżką przez dowolny obiekt, ale jeszcze nie został zebrany przez moduł odśmiecania pamięci.  
  
 Aby uzyskać lepszą wydajność `COR_HEAPOBJECT.address` pole jest `CORDB_ADDRESS` wartość, a nie icordebugvalue — interfejs wartość używana przez wiele interfejsu API debugowania. Aby uzyskać obiekt ICorDebugValue adresu podanego obiektu, można przekazać `CORDB_ADDRESS` wartość, która [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) metody.  
  
 Aby uzyskać lepszą wydajność `COR_HEAPOBJECT.type` pole jest `COR_TYPEID` wartość, a nie icordebugtype — interfejs wartość używana przez wiele interfejsu API debugowania. Aby uzyskać obiekt ICorDebugType dla Identyfikatora danego typu, możesz przekazać `COR_TYPEID` wartość, która [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metody.  
  
 `COR_HEAPOBJECT` Struktura zawiera interfejsu COM zliczonych odwołań. Jeśli pobierasz `COR_HEAPOBJECT` wystąpienia z modułu wyliczającego, wywołując [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metody, należy następnie zwolnij odwołanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

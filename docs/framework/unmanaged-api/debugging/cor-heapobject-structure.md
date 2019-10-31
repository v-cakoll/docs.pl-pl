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
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099075"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT — Struktura
Zawiera informacje o obiekcie na zarządzanym stosie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`size`|Łączny rozmiar obiektu w bajtach.|  
|`type`|Token [COR_TYPEID](cor-typeid-structure.md) , który reprezentuje typ obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 wystąpienia `COR_HEAPOBJECT` mogą być pobierane przez Wyliczenie obiektu interfejsu [ICorDebugHeapEnum](icordebugheapenum-interface.md) , który jest wypełniany przez wywołanie metody [ICorDebugProcess5:: EnumerateHeap —](icordebugprocess5-enumerateheap-method.md) .  
  
 Wystąpienie `COR_HEAPOBJECT` zawiera informacje o obiekcie aktywnym na zarządzanym stosie lub o obiekcie, który nie jest odblokowany przez żaden obiekt, ale nie został jeszcze zebrany przez moduł wyrzucania elementów bezużytecznych.  
  
 W celu uzyskania lepszej wydajności pole `COR_HEAPOBJECT.address` jest wartością `CORDB_ADDRESS`, a nie wartością interfejsu ICorDebugValue używaną w większości interfejsu API debugowania. Aby uzyskać obiekt ICorDebugValue dla danego adresu obiektu, można przekazać wartość `CORDB_ADDRESS` do metody [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .  
  
 W celu uzyskania lepszej wydajności pole `COR_HEAPOBJECT.type` jest wartością `COR_TYPEID`, a nie wartością interfejsu ICorDebugType używaną w większości interfejsu API debugowania. Aby uzyskać obiekt ICorDebugType dla danego identyfikatora typu, można przekazać wartość `COR_TYPEID` do metody [ICorDebugProcess5:: GetTypeForTypeID —](icordebugprocess5-gettypefortypeid-method.md) .  
  
 Struktura `COR_HEAPOBJECT` obejmuje interfejs COM liczony z odwołaniami. Jeśli pobierzesz wystąpienie `COR_HEAPOBJECT` z modułu wyliczającego, wywołując metodę [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) , należy następnie zwolnić odwołanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

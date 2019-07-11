---
title: CorGCReferenceType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cbecd5be9b1ac7c08e6970933a48eeb95f01a22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739383"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType — Wyliczenie
Określa źródło obiektu zebranych elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|`CorHandleStrong`|Dojście do silne odwołanie z tabeli uchwyt obiektu.|  
|`CorHandleStrongPinning`|Dojście do przypiętych silne odwołanie z tabeli uchwyt obiektu.|  
|`CorHandleWeakShort`|Dojście do słabe odwołanie z tabeli uchwyt obiektu.|  
|`CorHandleWeakRefCount`|Dojście do obiektu słabe zliczonych odwołań z tabeli uchwyt obiektu.|  
|`CorHandleStrongRefCount`|Dojście do obiektu zliczonych odwołań z tabeli uchwyt obiektu.|  
|`CorHandleStrongDependent`|Dojście do obiektu zależnego od tabelę uchwytów obiektu.|  
|`CorHandleStrongAsyncPinned`|Asynchroniczny obiekt przypięte z tabelę uchwytów obiektu.|  
|`CorHandleStrongSizedByref`|Silne dojście, który utrzymuje Przybliżony rozmiar zbiorowe zamknięcia wszystkich obiektów i korzenie obiektów w czasie kolekcji wyrzucania elementów.|  
|`CorReferenceStack`|Odwołanie z zarządzanego stosu.|  
|`CorReferenceFinalizer`|Odwołanie; kolejka finalizatorów.|  
|CorHandleStrongOnly|Zwróć tabelę uchwytów tylko silne odwołania. Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.|  
|`CorHandleWeakOnly`|Zwróć tabelę uchwytów jedynie słabe odwołania. Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.|  
|`CorHandleAll`|Zwraca wszystkie odwołania z tabeli dojście. Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.|  
  
## <a name="remarks"></a>Uwagi  
 `CorGCReferenceType` Wyliczenie jest używane w następujący sposób:  
  
- Jako wartość `type` pole [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) struktury, oznacza to źródło odniesienia lub uchwyt.  
  
- Jako `types` argument [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metody Określa typy dojścia do uwzględnienia w wyliczeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

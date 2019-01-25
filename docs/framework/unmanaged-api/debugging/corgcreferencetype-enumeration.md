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
ms.openlocfilehash: 54ac36f6d0dba92742ea7a7acfadc194930ccd74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516450"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType — Wyliczenie
Określa źródło obiektu zebranych elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
-   Jako wartość `type` pole [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) struktury, oznacza to źródło odniesienia lub uchwyt.  
  
-   Jako `types` argument [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metody Określa typy dojścia do uwzględnienia w wyliczeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

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
ms.openlocfilehash: 17d47b6242bb12ff5ca3cfbde3e4ec183b9c19fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793876"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType — Wyliczenie
Określa źródło obiektu, które ma zostać pobrane jako elementy bezużyteczne.  
  
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
|`CorHandleStrong`|Dojście do silnego odwołania z tabeli uchwytów obiektów.|  
|`CorHandleStrongPinning`|Dojście do przypiętego silnego odwołania z tabeli uchwytów obiektów.|  
|`CorHandleWeakShort`|Dojście do słabego odwołania z tabeli uchwytów obiektów.|  
|`CorHandleWeakRefCount`|Dojście do słabego odwołującego się obiektu z tabeli uchwytów obiektów.|  
|`CorHandleStrongRefCount`|Dojście do obiektu zliczanego odwołań z tabeli uchwytów obiektu.|  
|`CorHandleStrongDependent`|Dojście do obiektu zależnego z tabeli uchwytów obiektów.|  
|`CorHandleStrongAsyncPinned`|Asynchroniczny obiekt przypięty z tabeli uchwytów obiektu.|  
|`CorHandleStrongSizedByref`|Silne dojście, które utrzymuje przybliżony rozmiar całego rozłącznego zamykania wszystkich obiektów i katalogów głównych obiektów w czasie odzyskiwania pamięci.|  
|`CorReferenceStack`|Odwołanie z zarządzanego stosu.|  
|`CorReferenceFinalizer`|Odwołanie z kolejki finalizatora.|  
|CorHandleStrongOnly|Zwróć tylko silne odwołania z tabeli uchwytów. Ta wartość jest używana tylko przez metodę [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) .|  
|`CorHandleWeakOnly`|Zwróć tylko słabe odwołania z tabeli dojścia. Ta wartość jest używana tylko przez metodę [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) .|  
|`CorHandleAll`|Zwróć wszystkie odwołania z tabeli uchwytów. Ta wartość jest używana tylko przez metodę [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) .|  
  
## <a name="remarks"></a>Uwagi  
 Wyliczenie `CorGCReferenceType` jest używane w następujący sposób:  
  
- Jako wartość pola `type` struktury [COR_GC_REFERENCE](cor-gc-reference-structure.md) , wskazuje on źródło odwołania lub dojścia.  
  
- Jako argument `types` metody [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) określa typy dojść do uwzględnienia w wyliczeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)

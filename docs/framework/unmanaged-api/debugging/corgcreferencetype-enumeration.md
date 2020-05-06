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
ms.openlocfilehash: d156f103c3812c91da380e722a1c6c95d621df4c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860919"
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
 `CorGCReferenceType` Wyliczenie jest używane w następujący sposób:  
  
- Jako wartość `type` pola struktury [COR_GC_REFERENCE](cor-gc-reference-structure.md) wskazuje Źródło odwołania lub dojścia.  
  
- Jako `types` argument metody [ICorDebugProcess5:: EnumerateHandles —](icordebugprocess5-enumeratehandles-method.md) określa typy dojść do uwzględnienia w wyliczeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — wyliczenia](debugging-enumerations.md)

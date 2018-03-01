---
title: "CorGCReferenceType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b314580f7628eca68a3996aaafb362081c6ed705
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType — Wyliczenie
Określa źródło obiektu być zbierane z pamięci.  
  
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
|`CorHandleWeakRefCount`|Dojście do obiektu zliczane Odwołanie słabe z tabeli uchwyt obiektu.|  
|`CorHandleStrongRefCount`|Dojście do obiektu zliczane odwołanie z tabeli uchwyt obiektu.|  
|`CorHandleStrongDependent`|Dojście do obiektu zależnego z tabeli uchwyt obiektu.|  
|`CorHandleStrongAsyncPinned`|Asynchroniczny obiekt przypiętych z tabeli uchwyt obiektu.|  
|`CorHandleStrongSizedByref`|Dojście silne podtrzymujące przybliżone zbiorowe zamknięcia wszystkich obiektów i katalogi główne obiektu w momencie kolekcji pamięci.|  
|`CorReferenceStack`|Odwołanie z zarządzanego stosu.|  
|`CorReferenceFinalizer`|Odwołanie z kolejki finalizatora.|  
|CorHandleStrongOnly|Zwraca tylko silne odwołania z tabeli dojścia. Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.|  
|`CorHandleWeakOnly`|Zwraca tylko słabego odwołania z tabeli dojścia. Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.|  
|`CorHandleAll`|Zwraca wszystkie odwołania z tabeli dojścia. Ta wartość jest używana przez [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) tylko metody.|  
  
## <a name="remarks"></a>Uwagi  
 `CorGCReferenceType` Wyliczenie jest używane w następujący sposób:  
  
-   Jako wartość `type` pole [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) struktury wskazuje źródło dojście lub odwołanie.  
  
-   Jako `types` argument [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metody Określa typy dojść do uwzględnienia w wyliczeniu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

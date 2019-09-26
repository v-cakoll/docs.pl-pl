---
title: COR_GC_REFERENCE — Struktura
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc0b67621f77c0741e0b63b84ab1794530d6280b
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274224"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE — Struktura
Zawiera informacje o obiekcie, który ma zostać pobrany do pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`domain`|Wskaźnik do domeny aplikacji, do której należy dojście lub obiekt. Jego wartość może być `null`równa.|  
|`location`|Interfejs ICorDebugValue lub ICorDebugReferenceValue, który odnosi się do obiektu, który ma zostać pobrany jako bezużyteczny.|  
|`type`|Wartość wyliczenia [CorGCReferenceType](corgcreferencetype-enumeration.md) , która wskazuje, skąd pochodzi element główny. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
|`extraData`|Dodatkowe dane dotyczące obiektu, który ma zostać pobrany do pamięci. Te informacje są zależne od źródła obiektu, jak wskazano `type` w polu. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 Pole to CorGCReferenceType wartość wyliczenia, która wskazuje, skąd pochodzi odwołanie. [](corgcreferencetype-enumeration.md) `type` Określona `COR_GC_REFERENCE` wartość może odzwierciedlać dowolny z następujących rodzajów obiektów zarządzanych:  
  
- Obiekty ze wszystkich stosów zarządzanych`CorGCReferenceType.CorReferenceStack`(). Obejmuje to dynamiczne odwołania w kodzie zarządzanym, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.  
  
- Obiekty z tabeli uchwytów (`CorGCReferenceType.CorHandle*`). Obejmuje to ścisłe odwołania`HNDTYPE_STRONG` ( `HNDTYPE_REFCOUNT`i) oraz zmienne statyczne w module.  
  
- Obiekty z kolejki finalizatora (`CorGCReferenceType.CorReferenceFinalizer`). Obiekty główne kolejki finalizatora do momentu uruchomienia finalizatora.  
  
 `extraData` Pole zawiera dodatkowe dane w zależności od źródła (lub typu) odwołania. Możliwe wartości to:  
  
- `DependentSource`. Jeśli jest, `CorGCREferenceType.CorHandleStrongDependent`to pole jest obiektem, który, jeśli działa, jest katalogiem głównym obiektu, który ma `COR_GC_REFERENCE.Location`zostać odrzucony. `type`  
  
- `RefCount`. `type` Jeśli jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest liczbą odwołań do dojścia.  
  
- `Size`. `type` Jeśli jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiarem drzewa obiektów, dla którego Moduł wyrzucania elementów bezużytecznych oblicza elementy główne obiektu. Należy zauważyć, że to obliczenie nie jest zawsze aktualne.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

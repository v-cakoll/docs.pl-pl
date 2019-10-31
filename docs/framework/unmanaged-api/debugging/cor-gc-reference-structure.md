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
ms.openlocfilehash: 635cb0c003889beb2f78e8413189cbfc4b064175
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099139"
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
|`domain`|Wskaźnik do domeny aplikacji, do której należy dojście lub obiekt. Jego wartość może być `null`.|  
|`location`|Interfejs ICorDebugValue lub ICorDebugReferenceValue, który odnosi się do obiektu, który ma zostać pobrany jako bezużyteczny.|  
|`type`|Wartość wyliczenia [CorGCReferenceType](corgcreferencetype-enumeration.md) , która wskazuje, skąd pochodzi element główny. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
|`extraData`|Dodatkowe dane dotyczące obiektu, który ma zostać pobrany do pamięci. Te informacje są zależne od źródła obiektu, jak wskazano w polu `type`. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 Pole `type` jest wartością wyliczenia [CorGCReferenceType](corgcreferencetype-enumeration.md) , która wskazuje, skąd pochodzi odwołanie. Określona wartość `COR_GC_REFERENCE` może odzwierciedlać dowolny z następujących rodzajów obiektów zarządzanych:  
  
- Obiekty ze wszystkich zarządzanych stosów (`CorGCReferenceType.CorReferenceStack`). Obejmuje to dynamiczne odwołania w kodzie zarządzanym, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.  
  
- Obiekty z tabeli uchwytów (`CorGCReferenceType.CorHandle*`). Obejmuje to silne odwołania (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) oraz zmienne statyczne w module.  
  
- Obiekty z kolejki finalizatora (`CorGCReferenceType.CorReferenceFinalizer`). Obiekty główne kolejki finalizatora do momentu uruchomienia finalizatora.  
  
 Pole `extraData` zawiera dodatkowe dane w zależności od źródła (lub typu) odwołania. Możliwe wartości to:  
  
- `DependentSource`., Jeśli `type` jest `CorGCREferenceType.CorHandleStrongDependent`, to pole jest obiektem, który, jeśli działa, jest katalogiem głównym obiektu, który ma być odzyskiwany w `COR_GC_REFERENCE.Location`.  
  
- `RefCount`., Jeśli `type` jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest liczbą odwołań do dojścia.  
  
- `Size`., Jeśli `type` jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiarem drzewa obiektów, dla którego Moduł wyrzucania elementów bezużytecznych obliczy elementy główne obiektu. Należy zauważyć, że to obliczenie nie jest zawsze aktualne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

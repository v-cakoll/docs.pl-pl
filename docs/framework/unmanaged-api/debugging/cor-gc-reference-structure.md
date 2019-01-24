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
ms.openlocfilehash: 0375fdd6f86ae89171545cfdcb44ac37074084e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718718"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE — Struktura
Zawiera informacje dotyczące obiektu, który ma być zebranych elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`domain`|Wskaźnik do domeny aplikacji, do której należy dany dojścia lub obiektu. Wartość może być `null`.|  
|`location`|ICorDebugValue lub icordebugreferencevalue — interfejs, który odnosi się do obiektu, aby być zebranych elementów bezużytecznych.|  
|`type`|A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartość wyliczenia, która wskazuje, skąd pochodzą katalogu głównego. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
|`extraData`|Dodatkowe dane dotyczące obiekt zebranych elementów bezużytecznych. Te informacje zależy od źródła obiektu, wskazane przez `type` pola. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 `type` Pole jest [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartości wyliczenia, która wskazuje, skąd pochodzą odwołania. Konkretny `COR_GC_REFERENCE` wartość może odzwierciedlać jedną z następujących rodzajów obiekty zarządzane:  
  
-   Obiekty z wszystkie stosy zarządzane (`CorGCReferenceType.CorReferenceStack`). Obejmuje to odwołań na żywo w kodu zarządzanego, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.  
  
-   Obiekty z tabelę uchwytów (`CorGCReferenceType.CorHandle*`). Obejmuje to odwołań do silnych (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) i zmiennych statycznych w module.  
  
-   Obiekty z; kolejka finalizatorów (`CorGCReferenceType.CorReferenceFinalizer`). Elementy główne obiektów; kolejka finalizatorów, aż finalizator zostało uruchomione.  
  
 `extraData` Pole zawiera dane dodatkowe, w zależności od źródła (lub typ) odwołanie. Możliwe wartości to:  
  
-   `DependentSource`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongDependent`, to pole jest obiekt, który, jeśli jest aktywny, elementy główne obiekt zebranych elementów bezużytecznych w `COR_GC_REFERENCE.Location`.  
  
-   `RefCount`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest licznik odwołań uchwytu.  
  
-   `Size`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiar drzewa obiektów, dla którego moduł zbierający elementy bezużyteczne obliczana korzenie obiektów. Należy pamiętać, że to obliczenie nie zawsze aktualne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

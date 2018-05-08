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
ms.openlocfilehash: 732bc9d38ca0d6c2dc3f30603a722b7370034b80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE — Struktura
Zawiera informacje dotyczące obiektu, który ma być zbierane z pamięci.  
  
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
|`location`|ICorDebugValue lub ICorDebugReferenceValue — interfejs umożliwiająca obiektu ma być zbierane z pamięci.|  
|`type`|A [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartość wyliczenia wskazująca, skąd pochodzą katalogu głównego. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
|`extraData`|Dodatkowe dane dotyczące obiektu ma być zbierane z pamięci. Te informacje jest zależny od źródła obiektu, wskazywany przez `type` pola. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 `type` Pole jest [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartość wyliczenia wskazująca, skąd pochodzą odwołania. Określonego `COR_GC_REFERENCE` wartości można odzwierciedlać dowolną z następujących typów obiektów zarządzanych:  
  
-   Obiekty z wszystkie zarządzane stosy (`CorGCReferenceType.CorReferenceStack`). Dotyczy to na żywo odwołuje się do kodu zarządzanego, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.  
  
-   Obiekty z tabeli dojścia (`CorGCReferenceType.CorHandle*`). W tym silne odwołań (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) i zmienne statyczne w module.  
  
-   Obiekty w kolejce finalizatora (`CorGCReferenceType.CorReferenceFinalizer`). Kolejce finalizatora katalogów głównych obiektów, do momentu finalizator zostało uruchomione.  
  
 `extraData` Pole zawiera dodatkowe dane w zależności od źródłowego (lub typ) odwołanie. Możliwe wartości to:  
  
-   `DependentSource`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongDependent`, to pole jest obiekt, który jeśli aktywności, katalogów głównych obiektu ma być pobrane pamięci w `COR_GC_REFERENCE.Location`.  
  
-   `RefCount`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest liczba odwołań uchwytu.  
  
-   `Size`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiar drzewa obiektów, dla którego moduł zbierający elementy bezużyteczne obliczana katalogów głównych obiektów. Należy zwrócić uwagę, to obliczenie nie jest zawsze aktualny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

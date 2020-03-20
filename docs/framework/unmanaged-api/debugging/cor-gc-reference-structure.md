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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179317"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE — Struktura
Zawiera informacje o obiekcie, który ma być zbierane śmieci.  
  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`domain`|Wskaźnik do domeny aplikacji, do której należy dojście lub obiekt. Jego wartość `null`może być .|  
|`location`|Interfejs ICorDebugValue lub ICorDebugReferenceValue, który odpowiada obiektowi, który ma być zbierany z modułu.|  
|`type`|A [CorGCReferenceType](corgcreferencetype-enumeration.md) wartość wyliczenia, która wskazuje, skąd pochodzi katalog główny. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
|`extraData`|Dodatkowe dane dotyczące obiektu, który ma być zbierany na śmieci. Informacje te zależą od źródła obiektu, wskazanego `type` w polu. Aby uzyskać więcej informacji, zobacz sekcję: Uwagi.|  
  
## <a name="remarks"></a>Uwagi  
 Pole `type` jest wartością wyliczenia [CorGCReferenceType,](corgcreferencetype-enumeration.md) która wskazuje, skąd pochodzi odwołanie. Określona `COR_GC_REFERENCE` wartość może odzwierciedlać dowolny z następujących rodzajów obiektów zarządzanych:  
  
- Obiekty ze wszystkich zarządzanych stosów (`CorGCReferenceType.CorReferenceStack`). Obejmuje to odwołania na żywo w kodzie zarządzanym, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.  
  
- Obiekty z tabeli`CorGCReferenceType.CorHandle*`uchwytów ( ). Obejmuje to silne`HNDTYPE_STRONG` odwołania `HNDTYPE_REFCOUNT`( i ) i zmienne statyczne w module.  
  
- Obiekty z kolejki finalizatorów (`CorGCReferenceType.CorReferenceFinalizer`). Obiekty główne kolejki finalizacji, dopóki finalizator nie zostanie uruchomiony.  
  
 To `extraData` pole zawiera dodatkowe dane w zależności od źródła (lub typu) odwołania. Możliwe wartości:  
  
- `DependentSource`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongDependent`, to pole jest obiektem, który, jeśli żyje, `COR_GC_REFERENCE.Location`korzenie obiektu mają być zbierane w odpadach w .  
  
- `RefCount`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongRefCount`, to pole jest liczbą odwołań dojścia.  
  
- `Size`. Jeśli `type` jest `CorGCREferenceType.CorHandleStrongSizedByref`, to pole jest ostatnim rozmiarem drzewa obiektów, dla którego moduł zbierający elementy bezużyteczne obliczył katalogi główne obiektu. Należy zauważyć, że to obliczenie niekoniecznie jest aktualne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury debugowania](debugging-structures.md)
- [Debugging](index.md)

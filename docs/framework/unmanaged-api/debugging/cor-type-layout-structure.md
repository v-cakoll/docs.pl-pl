---
title: COR_TYPE_LAYOUT — Struktura
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b88a7b0672e15097c60afbe069ce5b78bd5c38d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408147"
---
# <a name="cortypelayout-structure"></a>COR_TYPE_LAYOUT — Struktura
Zawiera informacje o układzie obiektu w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`parentID`|Identyfikator typu nadrzędnego do tego typu. Będzie to identyfikator typu NULL (token1 = 0, token2 = 0), gdy odpowiada identyfikator typu <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|Wielkość podstawowa obiektu tego typu. Jest to łączny rozmiar obiektów o rozmiarze-variable.|  
|`numFields`|Liczba pól zawarte w obiektach tego typu.|  
|`boxOffset`|Jeśli ten typ jest opakowany, początku przesunięcia pól obiektu. W tym polu jest prawidłowa tylko dla typów wartości, takich jak podstawowych i struktury.|  
|`type`|CorElementType, do którego należy tego typu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `numFields` jest większa od zera, można wywołać [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) metody, aby uzyskać informacje o pola w tym typie. Jeśli `type` jest `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, lub `ELEMENT_TYPE_SZARRAY`, rozmiar obiektów tego typu jest zmienną i można przekazać [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) struktury do [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

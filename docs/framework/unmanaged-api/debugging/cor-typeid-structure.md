---
title: COR_TYPEID — Struktura
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273993"
---
# <a name="cor_typeid-structure"></a>COR_TYPEID — Struktura
Zawiera identyfikator typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`token1`|Pierwszy token.|  
|`token2`|Drugi token.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_TYPEID` Struktura jest zwracana przez wiele metod debugowania, które dostarczają informacji o obiektach, które mają być zbierane jako elementy bezużyteczne. Następnie można przekazać jako argument do innych metod debugowania, które zawierają dodatkowe informacje na temat tego elementu. Na przykład przez Wyliczenie obiektu [ICorDebugHeapEnum](icordebugheapenum-interface.md) można pobrać pojedyncze obiekty [COR_HEAPOBJECT](cor-heapobject-structure.md) , które reprezentują poszczególne obiekty na stercie zarządzanym. Następnie można przekazać `COR_TYPEID` wartość `COR_HEAPOBJECT.type` z pola do metody [ICorDebugProcess5:: GetTypeForTypeID —](icordebugprocess5-gettypefortypeid-method.md) , aby pobrać obiekt ICorDebugType, który zawiera informacje o typie obiektu.  
  
 `COR_TYPEID` Obiekt ma być nieprzezroczysty. Nie można uzyskać dostępu do poszczególnych pól ani manipulować nimi. Jego jedynym zastosowaniem jest jako identyfikator, który jest dostarczany jako `out` parametr w wywołaniu metody i który może z kolei być przekazywany do innych metod w celu dostarczenia dodatkowych informacji.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)

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
ms.openlocfilehash: 51104516008ffee0694c72733cb5f82b5ba6d8cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609460"
---
# <a name="cortypeid-structure"></a>COR_TYPEID — Struktura
Zawiera identyfikator typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`token1`|Pierwszy token.|  
|`token2`|Drugiego tokena.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_TYPEID` Struktury jest zwracany przez szereg metod debugowania, które zawierają informacje dotyczące obiektów zebranych elementów bezużytecznych. Go może być następnie przekazywany jako argument do innych metod debugowania, które zapewniają dodatkowe informacje na temat tego elementu. Na przykład, wyliczając [icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu, możesz pobrać poszczególne [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektami, które reprezentują poszczególne obiekty na zarządzanej stercie. Możesz następnie przekazać `COR_TYPEID` wartość z `COR_HEAPOBJECT.type` pole [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metodę, aby pobrać obiekt ICorDebugType, który zawiera informacje o typie o obiekcie.  
  
 A `COR_TYPEID` obiekt ma być nieprzezroczyste. Nie należy uzyskać dostępu do ani modyfikować jego poszczególne pola. Jej jedyny użycie jest jako identyfikator, który jest dostarczana jako `out` parametr w wywołaniu metody i który może z kolei można przekazać do innych metod, aby podać dodatkowe informacje.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

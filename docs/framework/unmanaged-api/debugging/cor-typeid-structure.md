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
ms.openlocfilehash: 426420175a7d05f39859b9e217a888a8c01b6d63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740507"
---
# <a name="cortypeid-structure"></a>COR_TYPEID — Struktura
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

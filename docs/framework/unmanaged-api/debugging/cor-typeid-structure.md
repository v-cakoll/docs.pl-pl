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
ms.openlocfilehash: 3d4e07fb3d0988838fde662f4bb7d4719cc2d50f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408343"
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
 `COR_TYPEID` Struktury jest zwracany przez liczbę metod debugowania, które zawierają informacje o obiektach być zbierane z pamięci. Go można następnie przekazać jako argument do innych metod debugowania, które znajdują się dodatkowe informacje o tym elemencie. Na przykład, wyliczając [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu, możesz pobrać poszczególnych [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów, które reprezentują poszczególnych obiektów na stercie zarządzanej. Można następnie przekazać `COR_TYPEID` wartość z `COR_HEAPOBJECT.type` do [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metoda pobierania obiektu ICorDebugType, który zawiera typ informacji o obiekcie.  
  
 A `COR_TYPEID` obiektu ma być nieprzezroczyste. Nie można uzyskać dostępu do lub modyfikowany w zakresie poszczególnych pól. Jest jego wyłącznie do użytku jako identyfikatora, który został dostarczony jako `out` parametr w wywołaniu metody i który może z kolei można przekazać do innych metod, aby podać dodatkowe informacje.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

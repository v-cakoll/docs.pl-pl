---
title: CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aebc6dfe4830e6477cda8fd279b8ef2a8040895c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149672"
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie
Określa atrybuty elementu [iassemblyname — interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu, kiedy jest tworzony przez [createassemblynameobject —](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|Wskazuje, że parametr przekazany jest tekstową tożsamości.|  
|`CANOF_SET_DEFAULT_VALUES`|Ustawia kilka wartości domyślne.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Sprawdza reguły zestawu friend (tylko nazwa i klucz publiczny). Ten element jest tylko do użytku wewnętrznego.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Kombinacji `CANOF_PARSE_DISPLAY_NAME` i `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flag. Ten element jest tylko do użytku wewnętrznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyName, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [CreateAssemblyNameObject, funkcja](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [Wyliczenia łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)

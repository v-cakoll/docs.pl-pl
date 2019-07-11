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
ms.openlocfilehash: 871ad81cd83c40d7299f39ede404e274b95b2ac0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778460"
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie
Określa atrybuty elementu [iassemblyname — interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu, kiedy jest tworzony przez [createassemblynameobject —](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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

---
title: "CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CREATE_ASM_NAME_OBJ_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords: CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61e9bea623e38b1416721773d8739bc6e6748909
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie
Określa atrybuty [IAssemblyName — interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu, gdy jest tworzony przez [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkcji.  
  
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
|`CANOF_PARSE_DISPLAY_NAME`|Wskazuje, że przekazany parametr jest tożsamości tekstowej.|  
|`CANOF_SET_DEFAULT_VALUES`|Ustawia kilka wartości domyślne.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Sprawdza, czy reguła zestawu friend (tylko nazwa i klucz publiczny). Ten element członkowski jest tylko do użytku wewnętrznego.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Kombinację `CANOF_PARSE_DISPLAY_NAME` i `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flagi. Ten element członkowski jest tylko do użytku wewnętrznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IAssemblyName, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [CreateAssemblyNameObject, funkcja](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [Wyliczenia łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)

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
ms.openlocfilehash: f6abb59c3aaec40a4e7b228b8c69147a2d454431
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108882"
---
# <a name="create_asm_name_obj_flags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS — Wyliczenie
Określa atrybuty obiektu [interfejsu IAssemblyName](iassemblyname-interface.md) , gdy jest konstruowany [przez funkcję](createassemblynameobject-function.md) myfunctionobject.  
  
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
|`CANOF_PARSE_DISPLAY_NAME`|Wskazuje, że przesłany parametr jest tożsamością tekstową.|  
|`CANOF_SET_DEFAULT_VALUES`|Ustawia kilka wartości domyślnych.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Weryfikuje regułę zaprzyjaźnionego zestawu (tylko nazwę i klucz publiczny). Ten element członkowski jest przeznaczony wyłącznie do użytku wewnętrznego.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Kombinacja flag `CANOF_PARSE_DISPLAY_NAME` i `CANOF_VERIFY_FRIEND_ASSEMBLYNAME`. Ten element członkowski jest przeznaczony wyłącznie do użytku wewnętrznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyName, interfejs](iassemblyname-interface.md)
- [CreateAssemblyNameObject, funkcja](createassemblynameobject-function.md)
- [Wyliczenia łączenia](fusion-enumerations.md)

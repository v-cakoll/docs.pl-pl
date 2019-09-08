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
ms.openlocfilehash: 9897e396424b9076da8f30c61b5a14cfa9539690
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795421"
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
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Kombinacja `CANOF_PARSE_DISPLAY_NAME` flag i `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` . Ten element członkowski jest przeznaczony wyłącznie do użytku wewnętrznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IAssemblyName, interfejs](iassemblyname-interface.md)
- [CreateAssemblyNameObject, funkcja](createassemblynameobject-function.md)
- [Wyliczenia łączenia](fusion-enumerations.md)

---
title: CorValidatorModuleType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
ms.openlocfilehash: 038e2ec20e5fd01edf9835080e0f7a15ec862fd9
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008940"
---
# <a name="corvalidatormoduletype-enumeration"></a>CorValidatorModuleType — Wyliczenie
Określa typ modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|Moduł jest nieprawidłowym typem.|  
|`ValidatorModuleTypeMin`|Minimalna wartość `CorValidatorModuleType` wyliczenia.|  
|`ValidatorModuleTypePE`|Moduł jest przenośnym plikiem wykonywalnym (PE).|  
|`ValidatorModuleTypeObj`|Moduł jest plikiem. obj.|  
|`ValidatorModuleTypeEnc`|Moduł to sesja debugera Edit-and-Continue.|  
|`ValidatorModuleTypeIncr`|Moduł jest tym, który został utworzony przyrostowo.|  
|`ValidatorModuleTypeMax`|Maksymalna wartość `CorValidatorModuleType` wyliczenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)

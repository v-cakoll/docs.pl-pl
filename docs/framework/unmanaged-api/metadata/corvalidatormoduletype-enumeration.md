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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04bed418d96658e29328cf2ce6bba445639b437f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750756"
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|Moduł jest nieprawidłowego typu.|  
|`ValidatorModuleTypeMin`|Minimalna wartość `CorValidatorModuleType` wyliczenia.|  
|`ValidatorModuleTypePE`|Moduł jest plikiem przenośny plik wykonywalny (PE).|  
|`ValidatorModuleTypeObj`|Moduł jest plikiem obj.|  
|`ValidatorModuleTypeEnc`|Moduł jest sesja debugera edit-and-continue.|  
|`ValidatorModuleTypeIncr`|Moduł to taki, który został skompilowany przyrostowo.|  
|`ValidatorModuleTypeMax`|Maksymalna wartość `CorValidatorModuleType` wyliczenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

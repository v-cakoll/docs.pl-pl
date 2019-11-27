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
ms.openlocfilehash: a8dc09ee9f0f0fd79060bb86c599ab40a285153b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448756"
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
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|Moduł jest nieprawidłowym typem.|  
|`ValidatorModuleTypeMin`|Minimalna wartość wyliczenia `CorValidatorModuleType`.|  
|`ValidatorModuleTypePE`|Moduł jest przenośnym plikiem wykonywalnym (PE).|  
|`ValidatorModuleTypeObj`|Moduł jest plikiem. obj.|  
|`ValidatorModuleTypeEnc`|Moduł to sesja debugera Edit-and-Continue.|  
|`ValidatorModuleTypeIncr`|Moduł jest tym, który został utworzony przyrostowo.|  
|`ValidatorModuleTypeMax`|Maksymalna wartość wyliczenia `CorValidatorModuleType`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

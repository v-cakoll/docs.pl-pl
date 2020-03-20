---
title: VariableLocationType, wyliczenie
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178362"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType, wyliczenie
Wskazuje natywny typ lokalizacji zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`VLT_REGISTER`|Zmienna znajduje się w rejestrze.|  
|`VLT_REGISTER_RELATIVE`|Zmienna znajduje się w lokalizacji pamięci względnej rejestru.|  
|`VLT_INVALID`|Zmienna nie jest przechowywana w rejestrze ani w lokalizacji pamięci względnej rejestru.|  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski `VariableLocationType` wyliczenia jest zwracany przez [metodę ICorDebugVariableHome::GetLocationType.](icordebugvariablehome-getlocationtype-method.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie, wyliczenia](debugging-enumerations.md)

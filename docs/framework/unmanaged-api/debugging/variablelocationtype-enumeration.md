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
ms.openlocfilehash: 861d5daa481132d3d6527e8d5fbccfab6436c5fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139120"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType, wyliczenie
Wskazuje typ lokalizacji natywnej zmiennej.  
  
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`VLT_REGISTER`|Zmienna jest w rejestrze.|  
|`VLT_REGISTER_RELATIVE`|Zmienna znajduje się w lokalizacji pamięci względnej do rejestracji.|  
|`VLT_INVALID`|Zmienna nie jest przechowywana w rejestrze ani w lokalizacji pamięci względnej dla rejestru.|  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski wyliczenia `VariableLocationType` jest zwracany przez metodę [ICorDebugVariableHome:: Getlocationtype](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

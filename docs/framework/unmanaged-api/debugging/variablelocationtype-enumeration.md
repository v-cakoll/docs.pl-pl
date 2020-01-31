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
ms.openlocfilehash: 1aa59ee559abff8006f0ac63a812e4315aa48154
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790310"
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
 Element członkowski wyliczenia `VariableLocationType` jest zwracany przez metodę [ICorDebugVariableHome:: Getlocationtype](icordebugvariablehome-getlocationtype-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)

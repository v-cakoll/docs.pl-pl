---
title: CorDebugNGenPolicy — Wyliczenie
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 826dfceb28512e4fd3157c432b7a4d94fba704fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097861"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy — Wyliczenie
Zapewnia wartość określającą, czy debuger ładuje obrazy natywne (NGen) z pamięci podręcznej obrazów natywnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|W aplikacji [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] użycie obrazów z lokalnej pamięci podręcznej obrazów natywnych jest wyłączone. W aplikacji klasycznej to ustawienie nie ma żadnego wpływu.|  
  
## <a name="remarks"></a>Uwagi  
 Wyliczenie `CorDebugNGENPolicy` jest używane przez metodę [ICorDebugProcess5:: EnableNGENPolicy —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) . Wyłączenie używania obrazów z lokalnej pamięci podręcznej obrazów natywnych zapewnia spójne środowisko debugowania przez zagwarantowanie, że debuger ładuje obrazy skompilowane JIT możliwością debugowania zamiast zoptymalizowanych obrazów natywnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

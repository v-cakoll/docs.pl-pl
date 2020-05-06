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
ms.openlocfilehash: 036d3f12b38c19259fefaba674d0f9025a58d688
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795758"
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
|`DISABLE_LOCAL_NIC`|W aplikacji ze sklepu Windows 8. x korzystanie z obrazów z lokalnej pamięci podręcznej obrazów natywnych jest wyłączone. W aplikacji klasycznej to ustawienie nie ma żadnego wpływu.|  
  
## <a name="remarks"></a>Uwagi  
 `CorDebugNGENPolicy` Wyliczenie jest używane przez metodę [ICorDebugProcess5:: EnableNGENPolicy —](icordebugprocess5-enablengenpolicy-method.md) . Wyłączenie używania obrazów z lokalnej pamięci podręcznej obrazów natywnych zapewnia spójne środowisko debugowania przez zagwarantowanie, że debuger ładuje obrazy skompilowane JIT możliwością debugowania zamiast zoptymalizowanych obrazów natywnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — wyliczenia](debugging-enumerations.md)

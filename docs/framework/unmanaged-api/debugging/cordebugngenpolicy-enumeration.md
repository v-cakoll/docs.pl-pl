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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ae40916807a86d1c9828080a6cb9e5c1d14c2ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671229"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy — Wyliczenie
Zawiera wartość określającą, czy debuger wczytuje obrazów macierzystych (NGen) z pamięci podręcznej obrazów natywnych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|W [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplikacji, użycie obrazów z pamięci podręcznej obrazów natywnych lokalnej jest wyłączona. W przypadku aplikacji klasycznej to ustawienie nie obowiązuje.|  
  
## <a name="remarks"></a>Uwagi  
 `CorDebugNGENPolicy` Wyliczenie jest używane przez [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) metody. Wyłączanie użycie obrazów z pamięci podręcznej obrazów natywnych lokalnej zapewnia spójne środowisko debugowania, zapewniając, że debuger ładuje debugowania obrazów kompilowanego dokładnie na czas, zamiast zoptymalizowane obrazy natywne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

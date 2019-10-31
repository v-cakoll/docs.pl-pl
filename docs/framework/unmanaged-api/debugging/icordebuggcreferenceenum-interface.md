---
title: ICorDebugGCReferenceEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 49f89f7d36e74b1fa5921230d7dc6d271d4c0883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134634"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum — Interfejs
Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|Pobiera określoną liczbę wystąpień [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) , które zawierają informacje o obiektach, które będą zbierane jako elementy bezużyteczne.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugGCReferenceEnum` implementuje interfejs "ICorDebugEnum".  
  
 Wystąpienie `ICorDebugGCReferenceEnum` jest wypełniane wystąpieniami [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) przez wywołanie metody [ICorDebugProcess5:: EnumerateGCReferences —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) . Obiekty [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) można wyliczyć przez wywołanie metody [ICorDebugGCReference:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) .  
  
 Obiekty [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) w kolekcji wypełnione przez tę metodę reprezentują trzy rodzaje obiektów:  
  
- Obiekty ze wszystkich zarządzanych stosów. Obejmuje to dynamiczne odwołania w kodzie zarządzanym oraz obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.  
  
- Obiekty z tabeli uchwytów. Obejmuje to silne odwołania (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) oraz zmienne statyczne w module.  
  
- Obiekty z kolejki finalizatora. Obiekty główne kolejki finalizatora do momentu uruchomienia finalizatora.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

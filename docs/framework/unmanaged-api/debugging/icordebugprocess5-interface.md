---
title: ICorDebugProcess5 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31ecea4857dabc55e8acd3c22a025895a686efcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931092"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 — Interfejs
Rozszerza interfejs ICorDebugProcess w celu obsługi dostępu do sterty zarządzanej w celu zapewnienia informacji na temat wyrzucania elementów bezużytecznych obiektów zarządzanych oraz do określenia, czy debuger ładuje obrazy z lokalnej pamięci podręcznej obrazów natywnych aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnableNGENPolicy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Ustawia wartość określającą sposób ładowania obrazów natywnych przez aplikację podczas działania w ramach zarządzanego debugera.|  
|[EnumerateGCReferences, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Pobiera moduł wyliczający dla wszystkich obiektów, które mają być zbierane jako elementy bezużyteczne w procesie.|  
|[EnumerateHandles, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Pobiera moduł wyliczający dla dojść do obiektów w procesie.|  
|[EnumerateHeap, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Pobiera moduł wyliczający dla obiektów na zarządzanym stosie.|  
|[EnumerateHeapRegions, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Pobiera moduł wyliczający dla regionów zarządzanego stosu.|  
|[GetArrayLayout, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Pobiera informacje o układzie tablicy w pamięci.|  
|[GetGCHeapInformation, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Pobiera wskaźnik do struktury [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) , która zawiera informacje o obiektach, które mają być odzyskiwane na zarządzanym stosie.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Pobiera wskaźnik do obiektu na zarządzanym stosie.|  
|[GetTypeFields, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Pobiera wskaźnik do tablicy zawierającej informacje o polu dla typu na podstawie jego identyfikatora typu.|  
|[GetTypeForTypeID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Pobiera obiekt typu, który zawiera informacje o obiekcie w oparciu o jego identyfikatory typów.|  
|[GetTypeID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Pobiera identyfikator typu dla obiektu pod określonym adresem.|  
|[GetTypeLayout, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs logicznie rozszerza interfejsy ICorDebugProcess, ICorDebugProcess2 i [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) .  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego, z innego komputera lub z innego procesu.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

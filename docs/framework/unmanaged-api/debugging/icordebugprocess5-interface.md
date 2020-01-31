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
ms.openlocfilehash: 263124db75abdc058d26ffb606a13fc711aed8bf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792303"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 — Interfejs
Rozszerza interfejs ICorDebugProcess w celu obsługi dostępu do sterty zarządzanej w celu zapewnienia informacji na temat wyrzucania elementów bezużytecznych obiektów zarządzanych oraz do określenia, czy debuger ładuje obrazy z lokalnej pamięci podręcznej obrazów natywnych aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnableNGENPolicy, metoda](icordebugprocess5-enablengenpolicy-method.md)|Ustawia wartość określającą sposób ładowania obrazów natywnych przez aplikację podczas działania w ramach zarządzanego debugera.|  
|[EnumerateGCReferences, metoda](icordebugprocess5-enumerategcreferences-method.md)|Pobiera moduł wyliczający dla wszystkich obiektów, które mają być zbierane jako elementy bezużyteczne w procesie.|  
|[EnumerateHandles, metoda](icordebugprocess5-enumeratehandles-method.md)|Pobiera moduł wyliczający dla dojść do obiektów w procesie.|  
|[EnumerateHeap, metoda](icordebugprocess5-enumerateheap-method.md)|Pobiera moduł wyliczający dla obiektów na zarządzanym stosie.|  
|[EnumerateHeapRegions, metoda](icordebugprocess5-enumerateheapregions-method.md)|Pobiera moduł wyliczający dla regionów zarządzanego stosu.|  
|[GetArrayLayout, metoda](icordebugprocess5-getarraylayout-method.md)|Pobiera informacje o układzie tablicy w pamięci.|  
|[GetGCHeapInformation, metoda](icordebugprocess5-getgcheapinformation-method.md)|Pobiera wskaźnik do struktury [COR_HEAPINFO](cor-heapinfo-structure.md) , która zawiera informacje o obiektach, które mają być odzyskiwane na zarządzanym stosie.|  
|[GetObject, metoda](icordebugprocess5-getobject-method.md)|Pobiera wskaźnik do obiektu na zarządzanym stosie.|  
|[GetTypeFields, metoda](icordebugprocess5-gettypefields-method.md)|Pobiera wskaźnik do tablicy zawierającej informacje o polu dla typu na podstawie jego identyfikatora typu.|  
|[GetTypeForTypeID, metoda](icordebugprocess5-gettypefortypeid-method.md)|Pobiera obiekt typu, który zawiera informacje o obiekcie w oparciu o jego identyfikatory typów.|  
|[GetTypeID, metoda](icordebugprocess5-gettypeid-method.md)|Pobiera identyfikator typu dla obiektu pod określonym adresem.|  
|[GetTypeLayout, metoda](icordebugprocess5-gettypelayout-method.md)|Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs logicznie rozszerza interfejsy ICorDebugProcess, ICorDebugProcess2 i [ICorDebugProcess3](icordebugprocess3-interface.md) .  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego, z innego komputera lub z innego procesu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

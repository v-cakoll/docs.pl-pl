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
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089241"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 — Interfejs
Rozszerza icordebugprocess — interfejs do obsługi dostępu do zarządzanej sterty, do dostarczania informacji dotyczących wyrzucania elementów bezużytecznych obiektów zarządzanych, a do określenia, czy debuger wczytuje obrazy z pamięci podręcznej obrazów natywnych lokalnej aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnableNGENPolicy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Ustawia wartość określającą, jak aplikacja ładuje obrazy natywne podczas uruchamiania w debugerze zarządzanych.|  
|[EnumerateGCReferences, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Pobiera moduł wyliczający dla wszystkich obiektów, które mają być jesdnostką zbierającą śmieci w procesie.|  
|[EnumerateHandles, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Pobiera moduł wyliczający dla obiektu uchwytów w procesie.|  
|[EnumerateHeap, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Pobiera moduł wyliczający dla obiektów na stosie zarządzanym.|  
|[EnumerateHeapRegions, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Pobiera moduł wyliczający dla regionów zarządzanego stosu.|  
|[GetArrayLayout, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Pobiera informacje o układ tablicy w pamięci.|  
|[GetGCHeapInformation, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Pobiera wskaźnik do [cor_heapinfo —](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) strukturę, która zawiera informacje o obiektach, które mają być jesdnostką zbierającą śmieci na stosie zarządzanym.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Pobiera wskaźnik do obiektu w zarządzanym stosie.|  
|[GetTypeFields, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Pobiera wskaźnik do tablicy, która zawiera informacje o polach typu na podstawie jego identyfikatora typu.|  
|[GetTypeForTypeID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Pobiera obiekt typu, który zawiera informacje dotyczące obiektu, w oparciu o ich identyfikatory typów.|  
|[GetTypeID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Pobiera identyfikator typu obiektu pod podanym adresem.|  
|[GetTypeLayout, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Pobiera informacje o układ obiektu w pamięci na podstawie jego identyfikatora typu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs rozszerza logicznie ICorDebugProcess, ICorDebugProcess2, i [icordebugprocess3 —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfejsów.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie z innego komputera lub od innego procesu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

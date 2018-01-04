---
title: "ICorDebugProcess5 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5
helpviewer_keywords: ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e26f50967f0fb70e0593584e3f175d20a7b213e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 — Interfejs
Umożliwia rozbudowywanie interfejsu ICorDebugProcess do obsługi dostępu do sterty zarządzanej, aby podać informacje o pamięci obiektów zarządzanych, oraz do ustalenia, czy debuger ładuje obrazów z pamięci podręcznej obrazów natywnych lokalnej aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnableNGENPolicy, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Ustawia wartość określającą, jak ładowania obrazów natywnych podczas uruchamiania w debugerze zarządzanych aplikacji.|  
|[EnumerateGCReferences, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Pobiera moduł wyliczający dla wszystkich obiektów, które mają być zbierane pamięci w procesie.|  
|[EnumerateHandles, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Pobiera moduł wyliczający dla obiekt dojść w procesie.|  
|[EnumerateHeap, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Pobiera moduł wyliczający dla obiektów na stercie zarządzanej.|  
|[EnumerateHeapRegions, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Pobiera moduł wyliczający dla regionów sterty zarządzanej.|  
|[GetArrayLayout, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Pobiera informacje o układzie tablicy w pamięci.|  
|[GetGCHeapInformation, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Pobiera wskaźnik do [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) struktury, który zawiera informacje o obiektach, które mają być zbierane pamięci na stercie zarządzanej.|  
|[GetObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Pobiera wskaźnik do obiektu na stercie zarządzanej.|  
|[GetTypeFields, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Pobiera wskaźnik do tablicy, zawierający pola informacji dla typu na podstawie jego identyfikatora typu.|  
|[GetTypeForTypeID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Pobiera obiekt typu, który dostarcza informacji na temat obiektu, w oparciu o ich identyfikatorów typu.|  
|[GetTypeID, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Pobiera identyfikator typu dla obiektu pod określonym adresem.|  
|[GetTypeLayout, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs logicznie rozszerza ICorDebugProcess, ICorDebugProcess2, i [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfejsów.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie z innego komputera lub od innego procesu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)

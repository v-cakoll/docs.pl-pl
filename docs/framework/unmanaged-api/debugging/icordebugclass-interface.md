---
title: ICorDebugClass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79e93a44f2cc532286a7e9b01fa32292a4e1c69a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass-interface1"></a>ICorDebugClass Interface1
Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest rodzajowy, `ICorDebugClass` reprezentuje bez wystąpień typu ogólnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModule — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Pobiera moduł, który definiuje tę klasę.|  
|[GetStaticFieldValue — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Pobiera wartość określonego pola statycznego.|  
|[GetToken — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Pobiera `TypeDef` token metadanych dla tej klasy.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugClass` Interfejsu reprezentuje bez wystąpień typu ogólnego. ICorDebugType — interfejs reprezentuje typu ogólnego. Na przykład `Hashtable<K, V>` może być reprezentowany przez `ICorDebugClass`, podczas gdy `Hashtable<Int32, String>` może być reprezentowany przez `ICorDebugType`.  
  
 Typy ogólne nie są reprezentowane przez oba `ICorDebugClass` i `ICorDebugType`. Drugim interfejs został wprowadzony w programie .NET Framework w wersji 2.0 na wypadek wystąpienia typu.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

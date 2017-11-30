---
title: ICorDebugHandleValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue
helpviewer_keywords: ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b56c23caaaed2bc63c724769db1198fd088f7f1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebughandlevalue-interface1"></a>ICorDebugHandleValue Interface1
Podklasa ICorDebugReferenceValue reprezentujący wartość odwołania, do których debuger został utworzony obsługę wyrzucanie elementów bezużytecznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dispose — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Zwalnia odwołuje się ta dojścia `ICorDebugHandleValue` obiektu bez jawnego zwolnienia wskaźnika interfejsu.|  
|[GetHandleType — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Pobiera wartość CorDebugHandleType, która opisuje rodzaj odwołuje się ta dojścia `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugReferenceValue` Obiektu jest unieważnienie podziału wykonywania debugowanego kodu. `ICorDebugHandleValue` Przechowuje odwołanie do podziału i kontynuacje, do momentu jego jawnego zwolnienia.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

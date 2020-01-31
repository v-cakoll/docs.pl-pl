---
title: ICorDebugAppDomain2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: 6f9bcec66ff613d19c1198ac9849ca28c978f537
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788946"
---
# <a name="icordebugappdomain2-interface"></a>ICorDebugAppDomain2, interfejs

Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami referencyjnymi. Ten interfejs jest rozszerzeniem interfejsu ICorDebugAppDomain.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetArrayOrPointerType, metoda](icordebugappdomain2-getarrayorpointertype-method.md)|Pobiera tablicę określonego typu lub wskaźnik lub odwołanie do określonego typu.|  
|[GetFunctionPointerType](icordebugappdomain2-getfunctionpointertype-method.md)|Pobiera wskaźnik do funkcji, która ma daną sygnaturę.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)

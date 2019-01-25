---
title: ICorDebugClass2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb70016560f453caf7a7a3eed3e1aa6b5fc9f0ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557373"
---
# <a name="icordebugclass2-interface1"></a>ICorDebugClass2 Interface1
Reprezentuje klasą rodzajową lub klasy z parametrem metody typu <xref:System.Type>. Ten interfejs rozszerza [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetParameterizedType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|Pobiera deklaracji typu dla tej klasy.|  
|[SetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|Ustawia wartość wskazującą, czy metoda jest zdefiniowany przez użytkownika kod dla każdej metody tej klasy.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugClass, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

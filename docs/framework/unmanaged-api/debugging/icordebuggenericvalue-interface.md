---
title: ICorDebugGenericValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2209c6e28c7749bd149902e5b696955ee7f13f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981988"
---
# <a name="icordebuggenericvalue-interface"></a>ICorDebugGenericValue — Interfejs

Podklasa klasy "ICorDebugValue", która ma zastosowanie do wszystkich wartości. Ten interfejs zapewnia metody Get i Set dla wartości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|Kopiuje wartość do określonego bufora.|  
|[SetValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|Kopiuje nowej wartości z określonego bufora.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugGenericValue` jest interfejsem podrzędnych, ponieważ jest bez — może być zastosowana zdalnie.  
  
 Dla typów odwołań wartość jest odwołanie, a nie treści odwołania.  
  
 Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

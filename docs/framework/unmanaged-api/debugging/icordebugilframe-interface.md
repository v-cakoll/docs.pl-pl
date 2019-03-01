---
title: ICorDebugILFrame — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a10c39d7df12c86b8fcf0fb40389c087f96e1ee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965987"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame — Interfejs

Reprezentuje ramkę stosu kodu języka intermediate language (MSIL) firmy Microsoft. Ten interfejs jest podklasą icordebugframe — interfejs.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Pobiera wartość wskazującą, czy jest bezpiecznie Ustaw wskaźnik instrukcji do określonej lokalizacji przesunięcia.|  
|[EnumerateArguments, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Pobiera moduł wyliczający dla argumentów w tej ramce.|  
|[EnumerateLocalVariables, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.|  
|[GetArgument, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Pobiera wartość określonego argumentu w tej ramce stosu MSIL.|  
|[GetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Pobiera wartość wskaźnika instrukcji i wartości bitowe połączenie, w tym artykule opisano, jak wartość wskaźnika instrukcji zostały pobrane.|  
|[GetLocalVariable, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Pobiera wartość określonej zmiennej lokalnej w tej ramki stosu MSIL.|  
|[GetStackDepth, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Nie zaimplementowano.|  
|[GetStackValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Nie zaimplementowano.|  
|[SetIP, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugILFrame` Interfejs jest wyspecjalizowane icordebugframe — interfejs. Jest używany zarówno dla ramki kodu MSIL i just-in-time (JIT) skompilowany ramek. Kompilowanego dokładnie na czas ramki zaimplementować obu `ICorDebugILFrame` interfejsu i icordebugnativeframe — interfejs.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

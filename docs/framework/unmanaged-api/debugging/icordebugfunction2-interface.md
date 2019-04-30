---
title: ICorDebugFunction2, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 159cebc76f732629ed84a3b6c9041cc15f8bbb69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763766"
---
# <a name="icordebugfunction2-interface"></a>ICorDebugFunction2, interfejs

Logicznie umożliwia rozbudowanie interfejsu programu ICorDebugFunction, aby zapewnić obsługę debugowania tylko mój kod krokowym, które pomija kod niezwiązany z użytkownikiem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateNativeCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|(Nie została jeszcze zaimplementowana.) Pobiera wskaźnik interfejsu do icordebugcodeenum —, który zawiera instrukcje kodu natywnego w funkcji odwołuje się ten obiekt icordebugfunction2 —.|  
|[GetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|Pobiera wartość wskazującą, czy ta funkcja jest oznaczona jako kod użytkownika.|  
|[GetVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|Pobiera Edytuj i Kontynuuj wersja tej funkcji.|  
|[SetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|Zaznacza tę funkcję tylko mój kod przechodzenie krok po kroku.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

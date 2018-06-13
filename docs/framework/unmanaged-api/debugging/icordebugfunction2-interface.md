---
title: ICorDebugFunction2 Interface1
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
ms.openlocfilehash: d765f87e36c98b5f664e84d85b883bc949fccf54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415337"
---
# <a name="icordebugfunction2-interface1"></a>ICorDebugFunction2 Interface1
Logicznie rozszerza interfejs ICorDebugFunction zapewnia obsługę tylko mój kod krokowym debugowania, który powoduje pominięcie kodu innych użytkowników.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateNativeCode, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|(Nie została jeszcze zaimplementowana.) Pobiera wskaźnika interfejsu do ICorDebugCodeEnum, który zawiera instrukcje kodu macierzystego w funkcji odwołuje się ten obiekt ICorDebugFunction2.|  
|[GetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|Pobiera wartość wskazującą, czy ta funkcja jest oznaczony jako kodu użytkownika.|  
|[GetVersionNumber, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|Pobiera wersję tej funkcji Edytuj i Kontynuuj.|  
|[SetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|Zaznacza tę funkcję tylko mój kod wykonywanie krok po kroku.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

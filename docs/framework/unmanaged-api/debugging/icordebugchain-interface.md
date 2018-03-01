---
title: ICorDebugChain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6000f6d91b3fe2325868b9af58740e1c4cd76127
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchain-interface1"></a>ICorDebugChain Interface1
Reprezentuje segment stosu wywołań fizycznych lub logicznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateFrames, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, zaczynając od ostatniego ramki.|  
|[GetActiveFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Pobiera aktywny (to znaczy najnowszych) ramki w łańcuchu.|  
|[GetCallee, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Pobiera łańcucha, która została wywołana przez ten łańcuch.|  
|[GetCaller, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Pobiera łańcuch, który wywołuje ten łańcuch.|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Nie jest zaimplementowana.|  
|[GetNext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Pobiera łańcuch następnej ramki dla wątku.|  
|[GetPrevious, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Pobiera łańcuch poprzedniej ramki dla wątku.|  
|[GetReason, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Pobiera przyczynę genesis tego wywołania łańcucha.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Pobiera rejestr dla active część ten łańcuch.|  
|[GetStackRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Pobiera zakres adresów segmentu stosu dla tego łańcucha.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Pobiera część wątku fizycznym, którego ten łańcuch wywołań.|  
|[IsManaged, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Pobiera wartość wskazującą, czy ten łańcuch działa kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 Ramki stosu w łańcuchu zajmować miejsca na stosie ciągłe i udostępnianie tego samego wątku i kontekstu. Łańcuch może reprezentować albo łańcuchów kodu zarządzane lub niezarządzane. Pusta `ICorDebugChain` wystąpienie reprezentuje łańcucha kodu niezarządzanego.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

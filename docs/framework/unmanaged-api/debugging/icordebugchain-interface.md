---
title: ICorDebugChain, interfejs1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bb716f1ad4087642a76dc84266ec6d3f46c1ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571207"
---
# <a name="icordebugchain-interface1"></a>ICorDebugChain, interfejs1
Reprezentuje segment stosu wywołań fizycznych lub logicznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateFrames, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, począwszy od najbardziej aktualną ramki.|  
|[GetActiveFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Pobiera aktywny (oznacza to, najbardziej aktualną) ramki w łańcuchu.|  
|[GetCallee, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Pobiera łańcucha, który został wywołany przez tego łańcucha.|  
|[GetCaller, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Pobiera łańcucha, który wywołuje ten łańcuch.|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Nie zaimplementowano.|  
|[GetNext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Pobiera łańcuch następnej ramki dla wątku.|  
|[GetPrevious, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Pobiera łańcuch poprzedniej ramki dla wątku.|  
|[GetReason, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Pobiera przyczynę genesis tego łańcucha wywoływania.|  
|[GetRegisterSet, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Pobiera rejestr dla aktywnego częścią tego łańcucha.|  
|[GetStackRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Pobiera zakres adresów segment stosu dla tego łańcucha.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Pobiera wątku fizycznym, ten łańcuch wywołań jest częścią.|  
|[IsManaged, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Pobiera wartość wskazującą, czy ten łańcuch działa dla kodu zarządzanego.|  
  
## <a name="remarks"></a>Uwagi  
 Ramki stosu w łańcuchu zajmują miejsce ciągłe stosu i używają tego samego wątku i kontekstu. Łańcuch może reprezentować albo łańcuchów kodu zarządzanego lub niezarządzanego. Pusta `ICorDebugChain` wystąpienie reprezentuje łańcuch kodu niezarządzanego.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

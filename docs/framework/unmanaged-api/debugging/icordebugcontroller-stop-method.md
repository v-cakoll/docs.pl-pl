---
title: "ICorDebugController::Stop — Metoda"
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
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a8699a54814b37cc03404b72330812f3eb2b2f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop — Metoda
Wykonuje wspólne Zatrzymaj wszystkie wątki uruchomione kodu zarządzanego w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwTimeoutIgnored`  
 Nie używany.  
  
## <a name="remarks"></a>Uwagi  
 `Stop`wykonuje kod stop współpracy na wszystkie wątki uruchomione zarządzanych w procesie. Podczas sesji debugowania tylko do zarządzanych wątków niezarządzane może kontynuować działanie (ale będą blokowane podczas próby wywołania kodu zarządzanego). Podczas sesji debugowania interop również zostaną zatrzymane niezarządzanych wątków. `dwTimeoutIgnored` Wartość jest obecnie zignorowana i potraktowana jako INFINITE (-1). Jeśli współpracy stop zakończy się niepowodzeniem z powodu zakleszczenia, wszystkie wątki są wstrzymane i E_TIMEOUT jest zwracany.  
  
> [!NOTE]
>  `Stop`jest to tylko synchroniczne metoda w interfejsie API debugowania. Gdy `Stop` zwraca wartość S_OK, proces został zatrzymany. Bez wywołania zwrotnego ma nadane uprawnienia do powiadamiania słuchaczy ogranicznika. Debuger musi wywołać [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) umożliwia wznowienie procesu.  
  
 Debuger obsługuje licznika stop. Gdy licznik przechodzi do zera, kontrolerem jest wznawiana. Każde wywołanie `Stop` lub każdego wysyłanego wywołania zwrotnego zwiększa licznik. Każde wywołanie `ICorDebugController::Continue` zmniejsza licznika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 

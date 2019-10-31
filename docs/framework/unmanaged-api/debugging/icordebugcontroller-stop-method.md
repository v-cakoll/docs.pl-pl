---
title: ICorDebugController::Stop — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: c8c6b40f7a9c63a577140209eed65436040addcb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125388"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop — Metoda
Wykonuje przerwanie w ramach wszystkich wątków, które uruchamiają kod zarządzany w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwTimeoutIgnored`  
 Nie używany.  
  
## <a name="remarks"></a>Uwagi  
 `Stop` wykonuje przerwanie w ramach wszystkich wątków uruchamiających kod zarządzany w procesie. W trakcie sesji debugowania tylko zarządzanej wątki niezarządzane mogą nadal działać (ale będą blokowane podczas próby wywołania kodu zarządzanego). W trakcie sesji debugowania międzyoperacyjności wątki niezarządzane również zostaną zatrzymane. Wartość `dwTimeoutIgnored` jest obecnie ignorowana i traktowana jako NIESKOŃCZONa (-1). Jeśli z powodu zakleszczenia nie powiedzie się, wszystkie wątki są zawieszone i zwracany jest E_TIMEOUT.  
  
> [!NOTE]
> `Stop` jest jedyną metodą synchroniczną w interfejsie API debugowania. Gdy `Stop` zwraca S_OK, proces jest zatrzymany. Nie podano wywołania zwrotnego, aby powiadomić detektory zatrzymania. Debuger musi wywołać [ICorDebugController:: Kontynuuj](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby umożliwić wznowienie procesu.  
  
 Debuger zachowuje licznik zatrzymania. Gdy licznik spadnie do zera, kontroler zostanie wznowiony. Każde wywołanie `Stop` lub każdego wysłanego wywołania zwrotnego zwiększa licznik. Każde wywołanie `ICorDebugController::Continue` zmniejsza licznik.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 363d8f7d8cf960fb23210225c4545f73d597d663
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912846"
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
 `Stop`wykonuje przerwanie w ramach wszystkich wątków uruchamiających kod zarządzany w procesie. W trakcie sesji debugowania tylko zarządzanej wątki niezarządzane mogą nadal działać (ale będą blokowane podczas próby wywołania kodu zarządzanego). W trakcie sesji debugowania międzyoperacyjności wątki niezarządzane również zostaną zatrzymane. `dwTimeoutIgnored` Wartość jest obecnie ignorowana i traktowana jako nieskończona (-1). Jeśli z powodu zakleszczenia nie powiedzie się, wszystkie wątki są zawieszone i zwracany jest E_TIMEOUT.  
  
> [!NOTE]
> `Stop`jest jedyną metodą synchroniczną w interfejsie API debugowania. Gdy `Stop` zwraca S_OK, proces jest zatrzymany. Nie podano wywołania zwrotnego, aby powiadomić detektory zatrzymania. Debuger musi wywołać [ICorDebugController:: Kontynuuj](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , aby umożliwić wznowienie procesu.  
  
 Debuger zachowuje licznik zatrzymania. Gdy licznik spadnie do zera, kontroler zostanie wznowiony. Każde wywołanie `Stop` lub każde wywoływane wywołanie zwrotne zwiększa licznik. Każde wywołanie `ICorDebugController::Continue` zmniejsza licznik.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

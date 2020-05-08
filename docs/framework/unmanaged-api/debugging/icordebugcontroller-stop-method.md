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
ms.openlocfilehash: bb7eee0997a6c8671693accf2c95e6e06e0a4f2e
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976580"
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
 `Stop`wykonuje przerwanie w ramach wszystkich wątków uruchamiających kod zarządzany w procesie. W trakcie sesji debugowania tylko zarządzanej wątki niezarządzane mogą nadal działać (ale będą blokowane podczas próby wywołania kodu zarządzanego). W trakcie sesji debugowania międzyoperacyjności wątki niezarządzane również zostaną zatrzymane. `dwTimeoutIgnored` Wartość jest obecnie ignorowana i traktowana jako nieskończona (-1). Jeśli z powodu zakleszczenia nie powiedzie się, wszystkie wątki są zawieszone, a E_TIMEOUT jest zwracana.  
  
> [!NOTE]
> `Stop`jest jedyną metodą synchroniczną w interfejsie API debugowania. Gdy `Stop` zwraca S_OK, proces jest zatrzymany. Nie podano wywołania zwrotnego, aby powiadomić detektory zatrzymania. Debuger musi wywołać [ICorDebugController:: Kontynuuj](icordebugcontroller-continue-method.md) , aby umożliwić wznowienie procesu.  
  
 Debuger zachowuje licznik zatrzymania. Gdy licznik spadnie do zera, kontroler zostanie wznowiony. Każde wywołanie `Stop` lub każde wywoływane wywołanie zwrotne zwiększa licznik. Każde wywołanie `ICorDebugController::Continue` zmniejsza licznik.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

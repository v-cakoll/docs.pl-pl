---
title: ICorDebugManagedCallback::DebuggerError — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137370"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError — Metoda
Powiadamia debuger, że wystąpił błąd podczas próby obsłużenia zdarzenia z aparatu plików wykonywalnych języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym wystąpiło zdarzenie.  
  
 `errorHR`  
 podczas Wartość HRESULT, która została zwrócona przez program obsługi zdarzeń.  
  
 `errorCode`  
 podczas Liczba całkowita, która określa błąd CLR.  
  
## <a name="remarks"></a>Uwagi  
 Proces może być umieszczony w trybie przekazywania, w zależności od charakteru błędu.  
  
 Wywołanie zwrotne `DebugError` wskazuje, że usługi debugowania zostały wyłączone z powodu błędu, dlatego debugery powinny udostępnić komunikat o błędzie dla użytkownika. [ICorDebugProcess:: GetId —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) będzie bezpieczne do wywołania, ale wszystkie inne metody, w tym [ICorDebug:: terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), nie powinny być wywoływane. Debuger powinien używać obiektów systemu operacyjnego do kończenia procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

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
ms.openlocfilehash: 9b96c0a2eca543b9e01ccf92b271b1aa7003c5c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781945"
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
  
 Wywołanie zwrotne `DebugError` wskazuje, że usługi debugowania zostały wyłączone z powodu błędu, dlatego debugery powinny udostępnić komunikat o błędzie dla użytkownika. [ICorDebugProcess:: GetId —](icordebugprocess-getid-method.md) będzie bezpieczne do wywołania, ale wszystkie inne metody, w tym [ICorDebug:: terminate](icordebug-terminate-method.md), nie powinny być wywoływane. Debuger powinien używać obiektów systemu operacyjnego do kończenia procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)

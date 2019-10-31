---
title: ICorDebugThread::GetCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: 8082b2a3654f1605f18f3b68f54464dc83c8e60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133489"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException — Metoda
Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppExceptionObject`  
 określoną Wskaźnik do adresu obiektu `ICorDebugValue`, który reprezentuje wyjątek, który jest aktualnie generowany przez kod zarządzany.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt wyjątku będzie istniał od momentu zgłoszenia wyjątku do końca bloku `catch`. Ocena funkcji, która jest wykonywana przez metody ICorDebugEval, spowoduje wyczyszczenie obiektu wyjątku podczas instalacji i przywrócenie go po zakończeniu.  
  
 Wyjątki mogą być zagnieżdżane (na przykład, jeśli wyjątek jest zgłaszany w filtr lub w ocenie funkcji), więc może istnieć wiele oczekujących wyjątków w pojedynczym wątku. `GetCurrentException` zwraca najbardziej aktualny wyjątek.  
  
 Obiekt i typ wyjątku mogą ulec zmianie w całym okresie istnienia wyjątku. Na przykład po wystąpieniu wyjątku typu x, środowisko uruchomieniowe języka wspólnego (CLR) może za mało pamięci i podnieść go do wyjątku braku pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

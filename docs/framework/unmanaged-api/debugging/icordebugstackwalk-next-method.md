---
title: ICorDebugStackWalk::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: b89e968e9b12943c8192af3b280f8bd321a02110
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378789"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next — Metoda
Przenosi obiekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) do następnej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Środowisko wykonawcze zostało pomyślnie odwiązane z następną ramką (Zobacz uwagi).|  
|E_FAIL|Nie można wykonać `ICorDebugStackWalk` zaawansowanego obiektu.|  
|CORDBG_S_AT_END_OF_STACK|Osiągnięto koniec stosu w wyniku tego elementu unwind.|  
|CORDBG_E_PAST_END_OF_STACK|Wskaźnik ramki znajduje się już na końcu stosu; w związku z tym nie można uzyskać dostępu do dodatkowych ramek.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 `Next`Metoda przesuwa `ICorDebugStackWalk` obiekt do ramki wywołującej tylko wtedy, gdy środowisko uruchomieniowe może odwinięcie bieżącej ramki. W przeciwnym razie obiekt przechodzi do następnej ramki, którą środowisko uruchomieniowe może przewinięcie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugStackWalk — Interfejs](icordebugstackwalk-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

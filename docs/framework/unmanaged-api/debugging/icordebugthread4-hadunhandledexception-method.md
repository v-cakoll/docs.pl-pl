---
title: ICorDebugThread4::HadUnhandledException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: 4d954057c519263da49f8aaeeeef6ab9402b6956
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378371"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException — Metoda
Wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 określoną Wskaźnik na adres uporządkowanego wyliczania struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Wątek miał nieobsługiwany wyjątek od momentu jego utworzenia.|  
|S_FALSE|Wątek nigdy nie miał nieobsłużonego wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek. Gdy wywołanie zwrotne nieobsłużonego wyjątku zostanie wyzwolone lub natywne dołączanie JIT jest inicjowane, ta metoda jest gwarantowana do zwrócenia S_OK. Nie ma gwarancji, że metoda [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) zwróci wyjątek nieobsłużony; Jednak jeśli proces nie był jeszcze kontynuowany po otrzymaniu wywołania zwrotnego nieobsłużonego wyjątku lub po dołączeniu do natywnego kompilatora JIT. Ponadto jest możliwe (Chociaż mało prawdopodobne), aby mieć więcej niż jeden wątek z nieobsługiwanym wyjątkiem w czasie, gdy zostanie wyzwolone Natywne Dołączanie JIT. W takim przypadku nie ma możliwości ustalenia, który wyjątek wyzwalał dołączenie JIT.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugThread4 — Interfejs](icordebugthread4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

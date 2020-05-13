---
title: ICorDebugManagedCallback3::CustomNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 8a4620e591cc80efb5c0fd53b0edf3a35849c421
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209763"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification — Metoda
Wskazuje, że zostało zgłoszone powiadomienie niestandardowego debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThread`  
 podczas Wskaźnik do wątku, który wywołał powiadomienie.  
  
 `pAppDomain`  
 podczas Wskaźnik do domeny aplikacji zawierającej wątek, który zgłosił powiadomienie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Kolejne wywołanie metody [ICorDebugThread4:: GetCurrentCustomDebuggerNotification —](icordebugthread4-getcurrentcustomdebuggernotification-method.md) powoduje pobranie obiektu wątku, który został przekazano do <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metody. Typ obiektu wątku musi być wcześniej włączony przez wywołanie metody [ICorDebugProcess3:: SetEnableCustomNotification —](icordebugprocess3-setenablecustomnotification-method.md) . Debuger może odczytać parametry specyficzne dla typu z pól obiektu wątku i może przechowywać odpowiedzi w polach.  
  
 Interfejs [ICorDebug](icordebug-interface.md) nie nakłada żadnych zasad dotyczących typów powiadomień ani ich zawartości, a semantyka powiadomień jest ściśle umową między debugerami, aplikacjami i .NET Framework.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugManagedCallback3 — Interfejs](icordebugmanagedcallback3-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

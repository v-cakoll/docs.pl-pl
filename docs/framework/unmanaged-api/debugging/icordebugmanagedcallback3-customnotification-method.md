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
ms.openlocfilehash: 078f90387a475559067d402610ec264f4076ae01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793265"
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
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Kolejne wywołanie metody [ICorDebugThread4:: GetCurrentCustomDebuggerNotification —](icordebugthread4-getcurrentcustomdebuggernotification-method.md) powoduje pobranie obiektu wątku, który został przesłany do metody <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>. Typ obiektu wątku musi być wcześniej włączony przez wywołanie metody [ICorDebugProcess3:: SetEnableCustomNotification —](icordebugprocess3-setenablecustomnotification-method.md) . Debuger może odczytać parametry specyficzne dla typu z pól obiektu wątku i może przechowywać odpowiedzi w polach.  
  
 Interfejs [ICorDebug](icordebug-interface.md) nie nakłada żadnych zasad dotyczących typów powiadomień ani ich zawartości, a semantyka powiadomień jest ściśle umową między debugerami, aplikacjami i .NET Framework.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback3, interfejs](icordebugmanagedcallback3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

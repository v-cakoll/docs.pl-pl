---
title: ICorDebugManagedCallback::LoadClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 5d35ab4610ffa04d15dd2404fdf8010308bcb42a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212740"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass — Metoda
Powiadamia debuger o załadowaniu klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do której Klasa została załadowana.  
  
 `c`  
 podczas Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne występuje tylko wtedy, gdy dla modułu zawierającego klasę włączono funkcję ładowania klasy. Ładowanie klasy jest zawsze włączone dla modułów dynamicznych.  
  
 `LoadClass`Wywołanie zwrotne zapewnia odpowiedni czas na powiązanie punktów przerwania z nowo wygenerowanymi klasami w modułach dynamicznych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [UnloadClass, metoda](icordebugmanagedcallback-unloadclass-method.md)
- [ICorDebugManagedCallback — Interfejs](icordebugmanagedcallback-interface.md)

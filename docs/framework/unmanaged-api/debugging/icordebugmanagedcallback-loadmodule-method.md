---
title: ICorDebugManagedCallback::LoadModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 21a97f140a41f8f380c1334652bc2417e19659c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777138"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>ICorDebugManagedCallback::LoadModule — Metoda
Powiadamia debuger o pomyślnym załadowaniu modułu środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do której moduł został załadowany.  
  
 `pModule`  
 podczas Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł CLR.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne `LoadModule` zapewnia odpowiedni czas na przeanalizowanie metadanych dla modułu, ustawienie flag kompilatora just-in-Time (JIT) lub włączenie lub wyłączenie wywołania zwrotnego ładowania klasy dla modułu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [UnloadModule, metoda](icordebugmanagedcallback-unloadmodule-method.md)
- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)

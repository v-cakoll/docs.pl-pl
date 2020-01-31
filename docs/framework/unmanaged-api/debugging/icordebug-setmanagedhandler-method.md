---
title: ICorDebug::SetManagedHandler — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 54ef1cab27a39de39b39996729be6b8160570745
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788970"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler — Metoda
Określa obiekt obsługi zdarzeń dla zdarzeń zarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallback`  
 podczas Wskaźnik do obiektu [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , który jest obiektem procedury obsługi zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 `SetManagedHandler` musi być wywoływana w czasie tworzenia.  
  
 Jeśli implementacja `ICorDebugManagedCallback` nie zawiera wystarczających interfejsów do obsługi zdarzeń debugowania dla debugowanej aplikacji, `SetManagedHandler` zwraca wynik HRESULT E_NOINTERFACE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](icordebug-interface.md)

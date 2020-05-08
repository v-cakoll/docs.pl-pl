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
ms.openlocfilehash: a197d260c55d24f906da7d7f2768bb7ba1ad751f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895344"
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
 `SetManagedHandler`musi być wywoływana w czasie tworzenia.  
  
 Jeśli `ICorDebugManagedCallback` implementacja nie zawiera wystarczających interfejsów do obsługi zdarzeń debugowania dla debugowanej aplikacji, `SetManagedHandler` zwraca wartość HRESULT równą E_NOINTERFACE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebug — Interfejs](icordebug-interface.md)

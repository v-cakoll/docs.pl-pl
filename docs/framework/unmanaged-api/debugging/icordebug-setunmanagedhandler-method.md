---
title: ICorDebug::SetUnmanagedHandler — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: cafa1c99a8988c199d866796911d1983aabb7208
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785067"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler — Metoda
Określa obiekt obsługi zdarzeń dla zdarzeń niezarządzanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallback`  
 podczas Wskaźnik do obiektu [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) , który reprezentuje procedurę obsługi zdarzeń dla niezarządzanych zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt obsługi zdarzeń dla zdarzeń niezarządzanych musi być ustawiony po wywołaniu [ICorDebug:: Initialize](icordebug-initialize-method.md) i przed dowolnymi wywołaniami [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) lub [ICorDebug::D ebugactiveprocess](icordebug-debugactiveprocess-method.md). Jednak w przypadku starszych celów nie jest wymagane Ustawianie obiektu obsługi zdarzeń dla zdarzeń niezarządzanych do momentu zgłoszenia pierwszego natywnego zdarzenia debugowania. Jeśli `ICorDebug::CreateProcess` ustawił flagę CREATE_SUSPENDED, natywne zdarzenia debugowania nie mogą być wysyłane do momentu wznowienia wątku głównego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebug, interfejs](icordebug-interface.md)

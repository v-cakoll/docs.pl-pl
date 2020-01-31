---
title: ICorDebugController::Terminate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: 851a127c117b826c271dd021c41cfdb36045a1ff
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783753"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate — Metoda
Kończy proces z określonym kodem zakończenia.  
  
> [!NOTE]
> Ta metoda jest otoką dla funkcji Win32 `TerminateProcess`. W tym celu `Terminate` używa kodu zakończenia w taki sam sposób, w jaki funkcja Win32 `TerminateProcess` używa tej metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `exitCode`  
 podczas Wartość liczbowa, która jest kodem zakończenia. Prawidłowe wartości liczbowe są zdefiniowane w Winbase. h.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli proces zostanie zatrzymany po wywołaniu `Terminate`, proces powinien być kontynuowany przy użyciu metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , aby debuger otrzymał potwierdzenie zakończenia za pośrednictwem wywołania zwrotnego [ICorDebugManagedCallback:: ExitProcess —](icordebugmanagedcallback-exitprocess-method.md) lub [ICorDebugManagedCallback:: ExitAppDomain —](icordebugmanagedcallback-exitappdomain-method.md) .  
  
> [!NOTE]
> Ta metoda nie jest implementowana przez domenę aplikacji. Oznacza to, że nie jest zaimplementowany na poziomie <xref:System.AppDomain>.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
